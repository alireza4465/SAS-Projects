/* Load the CARS dataset from SASHELP */
proc print data=sashelp.cars (obs=10);
    title "First 10 observations from SASHELP.CARS";
run;

/* Summary statistics of the dataset */
proc means data=sashelp.cars n mean std min max;
    var MSRP EngineSize Horsepower MPG_City MPG_Highway;
    title "Summary Statistics of Key Variables in SASHELP.CARS";
run;

/* Frequency distribution of car types */
proc freq data=sashelp.cars;
    tables Type / nocum;
    title "Frequency Distribution of Car Types in SASHELP.CARS";
run;

/* Correlation analysis between numerical variables */
proc corr data=sashelp.cars;
    var MSRP EngineSize Horsepower MPG_City MPG_Highway;
    title "Correlation Analysis of Key Variables in SASHELP.CARS";
run;

/* Scatter plot of Horsepower vs. MPG_City */
proc sgplot data=sashelp.cars;
    scatter x=Horsepower y=MPG_City / markerattrs=(symbol=CircleFilled color=blue size=12);
    title "Scatter Plot of Horsepower vs. MPG_City";
    xaxis label="Horsepower";
    yaxis label="MPG (City)";
run;
