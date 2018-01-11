# utl_creating_100_subgroup_datasets
A better way to create 100 subgroup output datasets? Keywords: sas sql join merge big data analytics macros oracle teradata mysql sas communities stackoverflow statistics artificial inteligence AI Python R Java Javascript WPS Matlab SPSS Scala Perl C C# Excel MS Access JSON graphics maps NLP natural language processing machine learning igraph DOSUBL DOW loop stackoverflow SAS community.
    SAS Forum: A better way to create 100 subgroup output datasets?

    github
    https://github.com/rogerjdeangelis/utl_creating_100_subgroup_datasets
    https://github.com/rogerjdeangelis/utl_do_over_merging_137_datasets

     Two solutions

         1. Dynamic code.
         2. Static code. Generate and paste code

    You can either use do_over to create repeated program code and
    paste into your program or you ca use it directly.

    We need a %do in open code;

    you can get the %do_over macro here
    tclay@ashlandhome.net  (541) 482-6435
    David Katz, M.S. www.davidkatzconsulting.com
    https://goo.gl/3r2mzc
    https://github.com/rogerjdeangelis/utl_sql_looping_or_using_arrays_in_sql_do_over_macro

    SAS Forum
    https://goo.gl/ENRPvp
    https://communities.sas.com/t5/SAS-Procedures/A-better-way-to-create-subgroups/m-p/426628

    INPUT   (20 groups of three numbers)
    =====

     WORK.HAVE total obs=60

        GRP    VAL

          1     67
          1     75
          1      4

          2      5
          2     20
          2      0

          3     38
          3     93
          3     90

          ...

         20     20
         20      7
         20      9


    PROCESS ( all the code)
    ========================

     1. Dynamic

       %array(data,values=1-20)
       data
          %do_over(data,phrase=data?);
          set have;
          select (grp);
            %do_over(data,phrase=when (?) output data?,between=%str(;));
          end;
       run;quit;

      2. Static

       %put %do_over(data,phrase=data?);

       %put %do_over(data,phrase=when (?) output data?,between=%str(;));

       Copy the strings from the log ito your program


    OUTPUT
    ======

     WORK.DATA1 total obs=3

        GRP   VAL

         1     67
         1     75
         1      4
        ...

     WORK.DATA20 total obs=3

       GRP    VAL

        20     20
        20      7
        20      9

     NOTE: There were 60 observations read from the data set WORK.HAVE.
     NOTE: The data set WORK.DATA1 has 3 observations and 2 variables.
     NOTE: The data set WORK.DATA2 has 3 observations and 2 variables.
     NOTE: The data set WORK.DATA3 has 3 observations and 2 variables.
     ....
     NOTE: The data set WORK.DATA20 has 3 observations and 2 variables.


    %array(data,values=1-20)
    %put %do_over(data,phrase=?);

       data1 data2 data3 data4 data5 data6 data7 data8 data9 data10
       data11 data12 data13 data14 data15 data16 data17 data18 data19 data20

    %put %do_over(sel,phrase=when (?) output data?,between=%str(;));

    when (1) output data1 ;
    when (2) output data2 ;
    when (3) output data3 ;
    when (4) output data4 ;
    when (5) output data5 ;
    when (6) output data6 ;
    when (7) output data7 ;
    when (8) output data8 ;
    when (9) output data9 ;
    when (10) output data10 ;
    when (11) output data11 ;
    when (12) output data12 ;
    when (13) output data13 ;
    when (14) output data14 ;
    when (15) output data15 ;
    when (16) output data16 ;
    when (17) output data17 ;
    when (18) output data18 ;
    when (19) output data19 ;
    when (20) output data20 ;

