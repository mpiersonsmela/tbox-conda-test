# About tbox-scan
A lightweight tool for discovering tboxes in a given FASTA sequence adapted from tbdb.io. Uses INFERNAL for prediction. Employs TBDB feature identification to identify likely specifier sequence. Provides predicted specifier region, most likely specifier, T-box sequence, and makes structure predictions. For transcriptional T-boxes, will also attempt to fold terminator structure. Feature refinement based on gene context and host organism tRNAs is not included in this tool. This tool is part of the T-box Annotation Database (TBDB, https://tbdb.io) collection. Currently only supports input files with a single FASTA header and sequence.  Accepts whole genomes as inputs. 

Additional code for advanced users who want to perform downstream gene analysis and tRNA matching is available at: https://github.com/mpiersonsmela/tbox

# Dependencies 
This program is written for unix operating systems and requires INFERNAL, python, biopython, and pandas. Installation of dependencies is easiest using conda in a conda environment. 

# Installation
    conda install -c bioconda tbox-scan
     
# Using tbox-scan 
  
    Usage: tbox-scan -f <Input FASTA file> [-options]

    Scan a fasta sequence file for T-boxes and predict specifier & T-box sequence.
              -- Default: Will use INFERNAL with RFAM00230 covariance model with basic output
              -- Example: tbox-scan  -f input.fa -o output_file.csv -v
    Dependencies: INFERNAL, biopython, python3, pandas.


    Options
      -f <file>  : input FASTA <file> (required) 
      -o <file>  : save final results in <file> as .csv
                      default: out.csv
      -i <file>  : save INFERNAL output predictions to .txt <file>
                      default: INFERNAL.txt
      -l <file>  : save a .txt log <file> of pipeline output
      -m <model#> : search for t-boxes using specified covariance model
                      1: RFAM model (RF00230.cm), works best on class I t-boxes (default)
                      2: TBDB model (TBDB001.cm), works best on class II t-boxes 
      -c <value> : score cutoff for INFERNAL model predictions (default = 15)
      -v         : save verbose output
      -s         : silence console output
      -h         : print out summary of available options

    Examples
        cd examples
        tbox-scan  -f genome_example1.fa -o output_file1.csv -m 1 -v
        tbox-scan  -f genome_example2.fa -o output_file2.csv -m 1 -s -c 100

# About this work 
Tbox-scan was written as an auxilliary tool for the T-box Annotation Database (https://tbdb.io). More information about how the database was built can be found in the Nucleic Acids Research article. If you have questions or issues running tbox-scan, post an issue or message me on twitter @syntbio. 

- Marchand, J. A., Pierson Smela, M. D., Jordan, T. H. H., Narasimhan, K. & Church, G. M. TBDB – A database of structurally annotated T-box riboswitch:tRNA pairs. Nucleic Acids Res. 2020 Sep 3; doi: 10.1093/nar/gkaa721


