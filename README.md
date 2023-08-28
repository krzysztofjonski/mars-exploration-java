# mars-exploration-1-1q2023

Looks like humanity will have a bright future after all: the colonization of Mars has finally started. But it is no small effort. To avoid wasting billions of dollars worth of equipment in space, a lot of simulation exercises need to be done – here on Earth.

To fully flesh out the Mars rovers software, sample maps are needed to calibrate its functions. This is where you come into the picture. Your team is selected to be a part of this wonderful adventure. Your first task is to create an application that can generate randomized maps of Mars, based on some input requirements. These requirements can change quickly, so you need to build a robust software that can handle changing requirements in a flexible way.

In this first iteration the following objects are to be placed on the map:

'#' - mountains: these are always multi-dimensional, and don't have a location preference (placed randomly), dimension growth: 3
'&' - pits: multi-dimensional objects, random placement, dimension growth: 10
'%' - minerals: single-dimensional object, placed next to mountains, dimension growth: 0
'*' - pockets of water: single dimensional objects, placed next to pits, dimension growth: 0

Tasks

1. Configuration module
   Create configuration objects based on the above requirements. Implement the MapConfigurationValidator interface that checks if a supplied configuration is valid. A MapConfiguration object is valid if it does not violate the above rules (for example, minerals defined as multi-dimensional is a violation) and the total number of elements to be generated is not greater than the amount defined by ElementToSpaceRatio (50%).

    1.Configuration objects for mountains, pits, minerals, and water are created in the Application.java file. A MapConfiguration object is created which contains the element configurations.

    2.The MapConfigurationValidator is implemented and it correctly validates a MapConfiguration.

    3.The MapConfigurationValidator implementation is covered by unit tests
2. Calculator module
   Implement the interfaces found in the Calculation folder. The DimensionCalculator helps to calculate the dimensions of a 2D array with a given size. It returns the smallest 2D array that can hold the specified number of elements, plus the dimension growth. For example, if the size is 20 and the dimensionGrowth is 3, it must return 8.

When calculating adjacent coordinates using CoordinateCalculator signatures, make sure to cover edge cases.

    1.The DimensionCalculator interface is implemented.

    2.The DimensionCalculator implementation is covered with unit tests.

    3.The CoordinateCalculator interface is implemented.

    4.The CoordinateCalculator implementation is covered with unit tests.
3. MapElements module
   Implement the functionality in the MapElements folder. This module covers the following areas:

Building and generating map elements.

Defining the element placement logic.

Generating the map.

Note the following:

-There is a distinction between building a single-dimensional or a multi-dimensional element.

-The MapElementBuilder builds one element at a time, while the MapElementsGenerator uses the builder to create multiple element.

-Placing a single-dimensional element is easy, you just need one square to be free. With multi-dimensional ones, you need to make sure the element fits into the required space (there are no elements that occupy space in the map in any direction from the starting coordinate).

-Map generation logic. The algorithm must start with the largest elements (mountains and pits) to be able to place smaller elements. If an element has a PreferredLocationSymbol, such as minerals and water, the algorithm must try to place those elements next to (adjacent) the specified symbol. Otherwise, the algorithm just gets a random coordinate, and tries to place the element. If it is successful, the element can be removed from the collection and the algorithm can proceed with the next. If the placement does not happen, the algorithm must try again with the same element with a new random coordinate, until it finds suitable coordinates.

    1.The createStringRepresentation method of the Map record is implemented. This method turns the multidimensional string representation of the Map (or MapElement) into a single string, for display purposes.

    2.The createStringRepresentation method of the Map record is covered with unit tests.

    3.The MapElementBuilder interface is implemented.

    4.The MapElementBuilder implementation is covered with unit tests.

    5.The MapElementsGenerator interface is implemented.

    6.The MapElementsGenerator implementation is covered with unit tests.

    7.The MapElementPlacer interface is implemented.

    8.The MapElementPlacer implementation is covered with unit tests.

    9.The MapGenerator interface is implemented.

    10.The MapGenerator implementation is covered with unit tests.
4. Output module
   Create an implementation of the MapFileWriter interface that can write a Map into a specified file.

    1.The MapFileWriter interface is implemented.

    2.The MapFileWriter implementation is covered with unit tests
5. Application
   Complete the Application.java file which wires up the application components. Create at least three sample maps from a given configuration.

    1.The Application.java class is completed.

    2.There are at least three sample maps written into files in a directory specified by the application.