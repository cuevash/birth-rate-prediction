# Fertility exploration and simple prediction

One of the mayor factors that determine the demography evolution of a country is the fertility rate (FR).
This exploration will be based in well collected data by the World Bank.

* Intro to the history of FR and its relatedness to the demography growth
* Process of selecting which data to use
  * World Bank has a huge number of social economics data that is well suited for an exploration of these concepts. At least it is expected that this data will contain mayor factors that determine at a gross level the FR.
* Selecting the characteristics to be further investigated
  * Typical process of reducing factors or predictors.
  * The important point here is to find the main factors that are driving the behavior of FR
* More in depth analysis of these factors
  * Using data science methods to determine how well and with which confidence these factors predict FR.
  * As a bonus use ensemble methods to compare the results.
* Conclusions

## Methodology

The data we have is cross-sectional and time sectional. We could use some more advanced techniques to consider both characteristics at the same time. But for this exercise we want to create something more simple, so we are going to concentrate on the cross sectional data and to get the most accurate picture we will use the most recent time for all data.
Looking at the data on the files we can see the latest year with information is the 2021. So we will use the data of that year to make our exercise of regression estimation.

We select the next attributes as good candidates to be good predictors of the fertility rate. We want to check whether the combination of some macroeconomics features plus the level of education of females are good predictors of the fertility rate. I have a good hunch that that is the case, but of course being a data guy I need to put some science behind that statement.

So, the list of attributes including the one to be predicted (Fertility rate, total) I chose are:

| FeatureID            | Description                                                                                              | Source                      |
| -------------------- | -------------------------------------------------------------------------------------------------------- | --------------------------- |
| SP.DYN.TFRT.IN       | Fertility rate, total (births per woman)                                                                 | Word Development Indicators |
| SE.PRM.CUAT.FE.ZS    | Educational attainment, at least completed primary, population 25+ years, female (%) (cumulative)        | Gender Statistics           |
| SE.SEC.CUAT.LO.FE.ZS | Educational attainment, at least completed lower secondary, population 25+, female (%) (cumulative)      | Gender Statistics           |
| SE.SEC.CUAT.PO.FE.ZS | Educational attainment, at least completed post-secondary, population 25+, female (%) (cumulative)       | Gender Statistics           |
| SE.SEC.CUAT.UP.FE.ZS | Educational attainment, at least completed upper secondary, population 25+, female (%) (cumulative)      | Gender Statistics           |
| SE.TER.CUAT.ST.FE.ZS | Educational attainment, at least completed short-cycle tertiary, population 25+, female (%) (cumulative) | Gender Statistics           |
| SL.TLF.CACT.FM.ZS    | Ratio of female to male labor force participation rate (%) (modeled ILO estimate)                        | Gender Statistics           |
| NY.GNP.PCAP.CD       | GNI per capita, Atlas method (current US$)                                                               | Word Development Indicators |
| SP.POP.TOTL          | Population, total                                                                                        | Word Development Indicators |


I realized that the features for education make the model somewhat more complex, on top of that I am not really satisfied that those features combined are the best indicator for female education. Obviously they are good because it gives some picture of the overall education participation of female, but I think a single feature that is some sort of average of those an others educational female features could reduce the number of features and also give a nice indicator of female participation in education.

Before coming up with my own feature I looked the World Bank and Voilà!! I found the perfect feature! ()

Evidently any feature or features that I choose will have some limitations, but is a bit of the scope of this study to explore in more depth which other combinations of features will be better predictors. It would be a nice exercise to do. But I leave it for another time.

The final list including the one to be predicted (Fertility rate, total) will be :

| FeatureID         | Description                                                                       | Source                      |
| ----------------- | --------------------------------------------------------------------------------- | --------------------------- |
| SP.DYN.TFRT.IN    | Fertility rate, total (births per woman)                                          | Word Development Indicators |
| SL.TLF.CACT.FM.ZS | Ratio of female to male labor force participation rate (%) (modeled ILO estimate) | Gender Statistics           |
| NY.GNP.PCAP.CD    | GNI per capita, Atlas method (current US$)                                        | Word Development Indicators |
| SP.POP.TOTL       | Population, total                                                                 | Word Development Indicators |
| SE.SCH.LIFE.FE    | Expected years of schooling, female                                               | Gender Statistics           |







Selected indicators for analysis and source
The IMF databases mentioned collect over 480 indicators from all countries and not all of them are relevant for
this purpose. There was a preference for broad macroeconomic and social indicators which are easy to
understand without much domain knowledge.

## Structure of project

* Python project
* Jupiter notebook that helps to explore the initial data and also to show the results of applying the ML methods
* README : A well-structured README that summarizes what this project is about, the sources use, the workflow followed, and the main conclusion reached.
  * This README should include:
    * Reference to the jupyter notebook if is online.
    * Reference to the blog entry, Medium and web page
    * Some projects that inspired this work
