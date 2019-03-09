TopologyBroker_denovo_RA
============================================
#Using TopologyBroker for denovo design of RA

The idea is to generate compact (globular) protein backbones threaded through RA theozymes.

RA theozyme is a conceptual copy of the RA95.5-8F active site tetrad from Obexer (DOI: 10.1038/nchem.2596).

"nuc/nucleophile" is always K

"sht/shuttle" is Y

"sup/support" is YST

"brd/bridge" is NQ

"lig/ligand" is Methodol

RA theozymes are built by docking individual components of the theozyme, attached to pieces of secondary structure, to TS form of Methodol substrate.
Docking is guided by collection of Rosetta constraints to promote formation of hydrogen bonding network between components of the theozyme (similar to RA95.5-8F active site).
In addition to HB network formation, rotamers of the side chain forming tetrad need to be the most favorable for given secondary structure context.
Having pregenerated ensemble of theozymes try to use TopologyBroker framework (DOI: 10.1371/journal.pone.0138220) in RosettaScripts to:

Step 0: generate pose of <= ~130 residues (to be fit on chip for large scale gene synthesis). Currently have to mutate individual components of theozyme before applying RigidChunkCM to match residue types (which is counterproductive according to BW)

Step 1: use RigidChunkCM to thread backbone through theozyme (in centroid mode)

Step 3: use AbinitioScript to generate some compact (globular) pose using rest of the pose

Step 4: use LoopCM to close any chainbreaks

....

Step X: somehow select backbones worthy of designing (ss content, topology looking similar to some native family etc.) and put sequence onto them.
