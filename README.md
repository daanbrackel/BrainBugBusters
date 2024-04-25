# BrainBugBusters
This tool was specifically designed to analyse clinical samples from FFPE specimens, however it can be used to analyse any bacterial sample. The outcome of this tool will result in a stacked barplot showing the abundance of every species and/or genus in your sample. This tool was designed with Oxford Nanopore sequencing reads (MinION), and was not tested with any other sequencing data. The input should be a folder containing all barcodes in a fastq.gz format. 

# Installing EMU and all needed scripts/dependencies

### Start by making a python environment:

```
conda create --name py37 python=3.7
``` 
```
conda activate py37
```

### Then install plotly and osfclient
```
pip install plotly
```
```
pip install osfclient
```

### Assuming you’re in your home directory, make an EMU folder

```
mkdir EMU
```

### Now run this command from your home directory:

```
pip install osfclient
export EMU_DATABASE_DIR=EMU
cd ${EMU_DATABASE_DIR}
osf -p 56uf7 fetch osfstorage/emu-prebuilt/emu.tar
tar -xvf emu.tar
```

### Now install EMU:

```
conda config --add channels defaults
conda config --add channels bioconda
conda config --add channels conda-forge
conda install emu
```

### Install all needed scripts
```
git clone https://github.com/daanbrackel/BrainBugBusters
cd BrainBugBusters
```
# Running the full pipeline
- Run the GhostCode.py (assuming your in the BrainBugBusters directory):
  ```
  python GhostCode.py "input_folder" "output_folder" "emu_database_dir" --threads 12
  ```
  the input folder must be a folder containing all barcode files in a fastq.gz format. The "emu_database_dir" is the EMU/ folder you made earlier in your home directory.
  
  or enter 
  ```
  python GhostCode.py --help
  ```
  for an explenation what each in/output is.
