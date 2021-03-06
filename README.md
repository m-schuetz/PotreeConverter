# Potree Converter

## Usage

### xyzrgb2bin
Converts xyz files with rgb data to binary files.
data has to be in following format (<> necessary, [] optional, will be ignored)

    <x> <y> <z> <r> <g> <b> [a]

for example:

    1.2312 4.311 5.12312 100 125 210
    1.2312 4.311 5.12312 123 124 125

usage:

    # rgbMaxValue:		indicates the range of rgb data. this value is used to normalize color values.
    xyzrgb2bin <sourcePath> <targetPath> <rgbMaxValue>

    # example
    xyzrgb2bin C:/pointclouds/pointcloud.xyz C:/pointclouds/pointcloud.bin 255


### PotreeConverter
Converts binary files to the potree file format.
Binary files must be in following format:

    <float:x><float:y><float:z><uchar:r><uchar:g><uchar:b><uchar:a>

floats are 4 byte, little endian<br>
uchars are 1 byte <br>
Each point takes 16 byte<br>


    # pointDensity:		specifies the distance between points at root level. Each subsequent level has half the point density from the previous level
    # maxRecursions:	number of levels
    PotreeConverter <sourcePath> <targetDir> <pointDensity> <maxRecursions>
    
    # example
    PotreeConverter C:/pointclouds/pointcloud.bin C:/pointclouds/converted 1.0 5
