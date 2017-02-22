# Download BAG #

Code for downloading the Dutch Buildings Register (*Basisadministratie Gebouwen*/BAG) and converting it to CSV format. 




## Building code ##

The programmes to convert the XML-files from the BAG to CSV-format are written
in C++ and need to be compiled. In order to compile the programmes libxml2 and
libgdal need to be installed. Under Ubuntu this can be done using:

```
sudo apt install libxml2-dev libgdal-dev
```

The binaries can then be built using

```
make build
```

## Downloading the BAG and converting it to CSV ##

```
make download
```

should download the BAG and

```
make csv 
```

should convert the XML-files to CSV-format. This generates a number of CSV-files. 


### data/panden.csv ###

Variable           | Type     | Description
-------------------|----------|--------------------------------------------------------------
id                 | string   | id of building (numeric; but too long (16 digits) to store in int/double)
bouwjaar           | integer  | year built
pandstatus         | string   | status of building
begin\_geldigheid  | date     | start date of validity record (format: `2016123100000000000`)
eind\_geldigheid   | date     | end date of validity; often empty
geometrie\_wkt     | string   | polygon of building in WKT format (rijksdriehoek coordinates)
x                  | double   | x coordinate of centroid of building (rijksdriehoek)
y                  | double   | y coordinate

### data/openbareruimte.csv ###

Stores public spaces, e.g. streets, squares, roards. 

Variable           | Type     | Description
-------------------|----------|--------------------------------------------------------------
id                 | string   | id of public space (numeric; but too long (16 digits) to store in int/double)
name               | string   | name public space
type               | string   | type of public space
woonplaats         | string   | town
begin\_geldigheid  | date     | start date of validity record (format: `2016123100000000000`)
eind\_geldigheid   | date     | end date of validity; often empty

### data/verblijfsobjecten.csv ###

Variable           | Type     | Description
-------------------|----------|--------------------------------------------------------------
id                 | string   | id of use object (numeric; but too long (16 digits) to store in int/double)
gebruiksdoel       | string   | use goal
oppervlakte        | integer  | area (square metres)
status             | string   | status
hoofdadres         | string   | id of main address (links to ?)
begin\_geldigheid  | date     | start date of validity record (format: `2016123100000000000`)
eind\_geldigheid   | date     | end date of validity; often empty
geometrie\_wkt     | string   | coordinate in WKT format (rijksdriehoek coordinates)
x                  | double   | x coordinate of centroid (rijksdriehoek)
y                  | double   | y coordinate of centroid (rijksdriehoek)

