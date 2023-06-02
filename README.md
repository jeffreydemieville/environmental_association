# Environmental Association
This repo is used to associate the EnvironmentLogger data (containing weather and other ambient condition sensors) from the Maricopa Field Scanner to the plant detections resulting from the PhytoOracle processing pipelines. 

## Download container
To download the environmental association container run:

```bash
singularity build environmental_association.simg docker://phytooracle/environmental_association:latest
```

You should now see a new file called ```environmental_association.simg``` within your working directory.

## Running the container
Run the container:

```bash
singularity run -B $(pwd):/mnt --pwd /mnt environmental_association.simg -s 14 -c sorghum -i FLIR
```

This command runs the container on FLIR (flirIrCamera) sensor data for the season 14 data collected on sorghum.

Command Line Arguments:

* Output directory (-o, --out_dir)
  * Required: False
  * Default: environmental_association

* Season during which data were collected (-s, --season)
  * Required: True
  * Choices: 10, 11, 12, 13, 14, 15, 16

* Crop name of data to download (-c, --crop)
  * Required: True
  * Choices: sorghum, lettuce

* Instrument (sensor) used to collect phenotype data (-i, --instrument)
  * Required: True
  * Choices: FLIR, PS2
