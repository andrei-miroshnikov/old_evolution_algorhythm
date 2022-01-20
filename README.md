The algorithm generates a population on the NxM field. Cells are generated with a random genome.
The field consists of 3x RGB:
  * R layer is responsible for the amount of organics in the environment (currently not used).
  * G layer of the amount of light entering the environment is used by cells when implementing the Foto gene as a multiplier to the resulting organic matter.
  * B layer of the amount of salt in the medium, used in the implementation of the Chemo gene as a multiplier to the resulting organics.

The following genes may be present in the genome:
* Power genes:
* Foto - a gene that transforms the energy of light in the environment into organic matter.
* Chemo - a gene that converts salt in the environment into organics.
* Eat - a gene that allows a cell to eat a cell adjacent to it, receiving a part of the organic matter contained in it.
  
* Movement genes move a cell in a given direction if it is not occupied by another cell:
* Up
*Down
  *Left
  *Right

Cells on the medium are stained in different colors, where R, G, B color channels are calculated as the number of Eat, Foto, Chemo genes per total number of nutrition genes, respectively. cells lacking nutrition genes are stained white.

During one iteration, the algorithm goes through all the cells in the environment, and if the cell does not have enough organic matter to share, it implements a random gene from its genome, but if there is enough organic matter, then it shares.

Division is possible only when there is at least one empty space next to the cell. During division, a new cell is created that has the genome of the parent, but with a random mutation.

Mutations can be of 4 types:
  * Without mutations - the cell inherits the parent's genome without changes.
  * SNP - in the genome there is a random replacement of one gene with another.
  * Deletion - a random part of the genome is removed.
  * Insertion - a random part of the genome is copied and inserted at the end of the genome.
  
The algorithm works until the entire population dies out or is stopped by the Ctrl + C combination. At the end of the work, life_data.csv is generated containing information about all cells and consists of their columns: Genome, the iteration on which was created, the index of the parent cell, age at the time of death.

Running the algorithm: run main.py


Libraries used in the code: numpy, pandas, cv2, collections, itertools, random. 

