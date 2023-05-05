Download Link: https://assignmentchef.com/product/solved-cse231-project-7-list-and-tuples-and-file-manipulation
<br>
<strong> Project 07</strong><strong>.</strong>

<strong>Assignment Overview</strong>

<ul>

 <li>List and Tuples</li>

 <li>File manipulation</li>

</ul>

<strong>Assignment Background</strong>

Modern medicine has improved greatly over the past few centuries. From treating infections to building our immune system to combat diseases that our ancestors were defenseless against. However, these treatments are very expensive and unfortunately very few individuals can afford it. For this reason, Medicaid was signed into a law back in 1965 to help patients of low income households by covering some of the medication expenses. The Centers for Medicare &amp; Medicaid Services have a record of its drug spending and utilization by their beneficiaries. This document records the annual total spending, prescriptions fill count, and unit count for each medication. The prescription fill count records how many medications were prescribed by a certified physician. The unit count indicates how many units for this medication were prescribed. Each prescription have certain units (number of pills, grams, milliliters or other units). For example, one prescription of Xanax can have 60 pills, i.e. 60 units.   For more information, see the interactive dashboard (<u><a href="https://www.cms.gov/Research-Statistics-Data-and-Systems/Statistics-Trends-and-Reports/Information-on-Prescription-Drugs/2015Medicaid.html">https://www.cms.gov/Research-Statistics-Data-and-Systems/Statistics</a><a href="https://www.cms.gov/Research-Statistics-Data-and-Systems/Statistics-Trends-and-Reports/Information-on-Prescription-Drugs/2015Medicaid.html">Trends-and-Reports/Information-on-Prescription-Drugs/2015Medicaid.html</a></u><a href="https://www.cms.gov/Research-Statistics-Data-and-Systems/Statistics-Trends-and-Reports/Information-on-Prescription-Drugs/2015Medicaid.html">)</a>.

For this project, you are tasked to build an interface which will show the user some medications covered by Medicaid and how much the medications cost. You must read the file that we provide of Medicaid Drug Expending Data from 2011 to 2015 and store into a list of tuples for the program to extract and process the information. We want to display a table with the information of each medication for each year. Also, we want to plot two charts presenting the top 10 most prescribed medications and another for the top 10 most covered or money spent by Medicaid.

<strong>Project Specifications</strong>

<ol>

 <li>You must implement the following functions:</li>

 <li><strong>open_file()</strong> prompts the user to enter a filename. The program will try to open a commaseparated value (csv) file. An error message should be shown if the file cannot be opened. This function will loop until it receives proper input and successfully opens the file. It returns a file pointer.</li>

 <li><strong>read_data(fp)</strong> receives a file pointer of the data file. For this project, we are only interested in the following columns:</li>

</ol>

<strong>column 0: year (int)  # convert year to an int column 1: brand (string) </strong>

<strong>column 3: total (float)  # total spending on that drug column 4: prescriptions (int) column 5: units (int) </strong>

In addition to these variables, you must compute two more values. In this function you need to compute the average cost per prescription as well as the average cost per unit. Only append the medications where they have defined numeric values for the total, prescriptions, <em>and</em> units.

This function returns a sorted list of tuples (we sort so we have a canonical ordering for Mimir testing). Each tuple should include the following data in the this order:

<strong>(year, brand, total, prescriptions, units, avg_cost_prescription, avg_cost_units) </strong>

<ol>

 <li><strong>get_year_list(year, data)</strong> This function receives the specified year (integer) and the list of tuples with the entire dataset, that is, the list returned by read_data. This function returns a sorted list of tuples with all the medications covered by Medicaid during the specified year.</li>

 <li><strong>top_ten_list(column, year_list) </strong>Receives column index (integer) and a list of tuples containing all the medications covered for a specific year, i.e. data returned from the get_year_list function. This function returns two lists: (list1) containing the brand names of the top 10 and (list2) the values in the specified column for the top 10 tuples reverse order. 3 is for Medicaid coverage, 4 is for number of prescriptions. Note that column n is in index n-1 of the tuple, so you should adjust it. Hint: sort the whole list in reverse order, slice off the top ten, and then create the two lists to return as a tuple (list1,list2).</li>

 <li><strong>display_table(year, year_list)</strong> This function displays the following information for each medication in a year (sorted by brand name, A-Z): brand name, number of prescriptions, average prescription cost, and the total spending per medication. Remember to use string formatting specified below to properly display the results. Divide the total spending by 1000 to make the output look nicer.</li>

 <li><strong>main()</strong> This function is the main part of the program. You need to open the file and pass the file pointer to the read_data function. Then you need to prompt for a year to search in the data list and send it to the display_table function to output. Then you prompt whether you want to plot the top 10 medications in the data list. Hint: Make sure that the entered year exists in the data file (validate the input!)</li>

 <li>Requirements</li>

 <li>Use <strong>sorted()</strong> and <strong>itemgetter()</strong> For the top 10 lists, sort the list of tuples from largest item first, if two tuples have the same value, sort by brand name. Hint: both top 10 functions will sort; in the example below, <strong>y</strong> is the index of the brand name.</li>

</ol>

from operator import itemgetter

sorted_lst = sorted(num_list, key=itemgetter(x,y), reverse=True)

<ol>

 <li>For display_table, use the following formatting. To get commas in numbers place a comma immediately after the field width, e.g. {:10,d} or {:10,.2f}:

  <ol>

   <li>The header should be centered on 80 spaces</li>

   <li>Medication Brand Name = 35 spaces, left justified</li>

  </ol></li>

</ol>

<ul>

 <li>Prescription = 15 spaces, right justified with comma between 3 digits</li>

</ul>

<ol>

 <li>Average Prescription Cost = 20 spaces, right justified, 2 decimal digits</li>

 <li>Total spending by Medicaid = 15 spaces, right justified, 2 decimal digits, with comma between 3 digits (this value is in thousands)</li>

 <li><strong>plot_top_ten(x, y, title, xlabel, ylabel)</strong> You must use this provided function to plot the results. This function has 5 parameters: the list of medication brand names <strong>x</strong>, the list of numeric values<strong> y</strong>, the plot <strong>title</strong>, the x-axis title <strong>xlabel</strong>, and the y-axis title <strong>ylabel</strong>. Note that this function will be used to draw both plots, one for the most prescribed medications and the other for the highest prescription cost.</li>

</ol>

<ol>

 <li><strong>Read the file only once. </strong>Specifically, you read the file once in the read_data function and store the information in a list.  For the rest of the program you get information from lists—you don’t go back and re-read the file.</li>

</ol>

<ol>

 <li><strong>Want an extra challenge? </strong>Using list comprehension you can write the function get_year_list in one line that is readable.<strong> Deliverables</strong></li>

</ol>

The deliverable for this assignment is the following file:       proj07.py – the source code for your Python program

Be sure to use the specified file name and to submit it for grading via Mimir before the project deadline.

<strong>Read_data function test: </strong>

fp = open(“medicaid_spending_small.csv”,”r”)

read_data(fp)

returns:

[(2011, ‘Abilify’, 1715769087.0, 3007841, 98263157, 570.4321096095173,

17.460960337352077), (2011, ‘Adderall XR’, 376431028.8, 1613783, 55728012,

233.26000385429765, 6.7547901906136545), (2011, ‘Advair Diskus’, 578947345.1,

2462514, 150975222, 235.10418421986637, 3.8347176273733186), (2011,

‘Carbamazepine’, 11436846.03, 618588, 99627263, 18.48863222370948,

0.11479634876650179), (2011, ‘Clobetasol Propionate’, 10157350.16, 379057,

20788507, 26.796366140184723, 0.4886041195743398), (2011, ‘Flovent HFA’, 280559007.5, 1924032, 22347142, 145.81826471701095, 12.55458114062192),

(2011, ‘Humalog’, 128527266.2, 602919, 10883844, 213.17501389075483,

11.808995626912697), (2011, ‘Invega’, 283641529.9, 380435, 8945035,

745.5715954105168, 31.709381785538007), (2011, ‘Lantus’, 410789437.2,

2204518, 36172479, 186.33979727087734, 11.35640820193717), (2011, ‘Lyrica’,

208052625.3, 1080100, 75574568, 192.6234842144246, 2.752944949682015), (2011,

‘Methylphenidate ER’, 226032289.6, 1332576, 44673828, 169.6205616790337, 5.0596131945531955), (2011, ‘Morphine Sulfate’, 20089793.94, 576161,

31066801, 34.86836828594785, 0.6466643907108428), (2011, ‘Proair HFA’,

221936930.0, 4784692, 44759787, 46.384789240352355, 4.9584000477929), (2011,

‘Seroquel XR’, 371592404.1, 952900, 36177324, 389.9594963794732,

10.271417645484227), (2011, ‘Spiriva’, 215473653.8, 936931, 28940707,

229.97814545574863, 7.445348650259305), (2011, ‘Suboxone’, 318060139.8,

1198265, 48316821, 265.4338896654747, 6.582803529230534), (2011, ‘Symbicort’,

128740153.2, 621462, 6467805, 207.15691900711548, 19.904767258753164), (2011,

‘Truvada’, 457327611.8, 427891, 12715594, 1068.794650506788,

35.96588659562424), (2011, ‘Ventolin HFA’, 199072297.7, 4889379, 95528093,

40.715251916449915, 2.08391365773417), (2011, ‘Vyvanse’, 385235408.5,

2453085, 75585425, 157.04119853164485, 5.096689057447253), (2013, ‘Enbrel’, 255847098.5, 108123, 470496, 2366.259708850106, 543.7816655189417)]

<strong>Get_year_list function test: </strong>fp = open(“medicaid_spending_small.csv”,”r”) data = read_data(fp) get_year_list(2011,data)

returns:

[(2011, ‘Abilify’, 1715769087.0, 3007841, 98263157, 570.4321096095173,

17.460960337352077), (2011, ‘Adderall XR’, 376431028.8, 1613783, 55728012,

233.26000385429765, 6.7547901906136545), (2011, ‘Advair Diskus’, 578947345.1,

2462514, 150975222, 235.10418421986637, 3.8347176273733186), (2011,

‘Carbamazepine’, 11436846.03, 618588, 99627263, 18.48863222370948,

0.11479634876650179), (2011, ‘Clobetasol Propionate’, 10157350.16, 379057,

20788507, 26.796366140184723, 0.4886041195743398), (2011, ‘Flovent HFA’,

280559007.5, 1924032, 22347142, 145.81826471701095, 12.55458114062192),

(2011, ‘Humalog’, 128527266.2, 602919, 10883844, 213.17501389075483,

11.808995626912697), (2011, ‘Invega’, 283641529.9, 380435, 8945035,

745.5715954105168, 31.709381785538007), (2011, ‘Lantus’, 410789437.2,

2204518, 36172479, 186.33979727087734, 11.35640820193717), (2011, ‘Lyrica’,

208052625.3, 1080100, 75574568, 192.6234842144246, 2.752944949682015), (2011,

‘Methylphenidate ER’, 226032289.6, 1332576, 44673828, 169.6205616790337,

5.0596131945531955), (2011, ‘Morphine Sulfate’, 20089793.94, 576161,

31066801, 34.86836828594785, 0.6466643907108428), (2011, ‘Proair HFA’, 221936930.0, 4784692, 44759787, 46.384789240352355, 4.9584000477929), (2011,

‘Seroquel XR’, 371592404.1, 952900, 36177324, 389.9594963794732,

10.271417645484227), (2011, ‘Spiriva’, 215473653.8, 936931, 28940707,

229.97814545574863, 7.445348650259305), (2011, ‘Suboxone’, 318060139.8,

1198265, 48316821, 265.4338896654747, 6.582803529230534), (2011, ‘Symbicort’,

128740153.2, 621462, 6467805, 207.15691900711548, 19.904767258753164), (2011,

‘Truvada’, 457327611.8, 427891, 12715594, 1068.794650506788,

35.96588659562424), (2011, ‘Ventolin HFA’, 199072297.7, 4889379, 95528093,

40.715251916449915, 2.08391365773417), (2011, ‘Vyvanse’, 385235408.5, 2453085, 75585425, 157.04119853164485, 5.096689057447253)]




<strong>Top_ten_list function test: </strong>fp = open(“medicaid_spending_small.csv”,”r”) data = read_data(fp)

list_2011 = get_year_list(2011,data) top_ten_list(3,list_2011)

returns:

[‘Abilify’, ‘Advair Diskus’, ‘Truvada’, ‘Lantus’, ‘Vyvanse’, ‘Adderall XR’,

‘Seroquel XR’, ‘Suboxone’, ‘Invega’, ‘Flovent HFA’]

[1715769087.0, 578947345.1, 457327611.8, 410789437.2, 385235408.5,

376431028.8, 371592404.1, 318060139.8, 283641529.9, 280559007.5]

<strong>Test Case 1: </strong>

Input a file name: medicaid_spending_small.csv

Medicaid drug spending 2011 – 2015




Enter a year to process (‘q’ to terminate): 2011

Drug spending by Medicaid in 2011

Medication                           Prescriptions   Prescription Cost          Total

Abilify                                  3,007,841              570.43   1,715,769.09

Adderall XR                              1,613,783              233.26     376,431.03

Advair Diskus                            2,462,514              235.10     578,947.35

Carbamazepine                              618,588               18.49      11,436.85

Clobetasol Propionate                      379,057               26.80      10,157.35

Flovent HFA                              1,924,032              145.82     280,559.01

Humalog                                    602,919              213.18     128,527.27

Invega                                     380,435              745.57     283,641.53

Lantus                                   2,204,518              186.34     410,789.44

Lyrica                                   1,080,100              192.62     208,052.63

Methylphenidate ER                       1,332,576              169.62     226,032.29

Morphine Sulfate                           576,161               34.87      20,089.79

Proair HFA                               4,784,692               46.38     221,936.93

Seroquel XR                                952,900              389.96     371,592.40

Spiriva                                    936,931              229.98     215,473.65

Suboxone                                 1,198,265              265.43     318,060.14 Symbicort                                  621,462              207.16     128,740.15

Truvada                                    427,891            1,068.79     457,327.61

Ventolin HFA                             4,889,379               40.72     199,072.30 Vyvanse                                  2,453,085              157.04     385,235.41  Do you want to plot the top 10 values (yes/no)? no

Enter a year to process (‘q’ to terminate): q




<strong>Test Case 2: </strong>

Input a file name: xxx

Unable to open the file. Please try again.

Input a file name: test.csv

Unable to open the file. Please try again.

Input a file name: medicaid_spending.csv

Medicaid drug spending 2011 – 2015

Enter a year to process (‘q’ to terminate): year Invalid Year. Try Again!

Enter a year to process (‘q’ to terminate): 2015

Drug spending by Medicaid in 2015

Medication                           Prescriptions   Prescription Cost          Total

Abilify                                  2,074,321              978.44   2,029,596.06

Adderall XR                              1,805,993              248.65     449,064.90

Advair Diskus                            1,758,551              330.32     580,892.33

Advate                                      16,979           20,828.38     353,645.10

Anucort-HC                                  18,364              273.61       5,024.49

Aripiprazole                               947,738              638.50     605,129.20

Ativan                                       7,168              734.32       5,263.61

Atripla                                    265,692            2,269.63     603,023.28

Avastin                                    144,610            1,297.06     187,568.41

Carbamazepine                              585,130               64.50      37,741.07

Clindamycin Phos-Benzoyl Perox              10,413              630.46       6,564.98

Clobetasol Propionate                      741,509              193.99     143,846.67

Complera                                   138,938            2,255.99     313,442.46

Copaxone                                    51,497            5,418.03     279,012.52

Daraprim                                     2,585            6,075.41      15,704.94

Demerol                                     48,806              100.42       4,900.98

Econazole Nitrate                          218,702              211.28      46,206.96

Enbrel                                     136,508            3,204.75     437,474.12

Epitol                                      58,483               46.27       2,706.08

Epzicom                                    117,317            1,205.16     141,386.15

Fentanyl Citrate                           474,760              116.52      55,317.74

Flovent HFA                              2,264,825              194.88     441,361.06

Gleevec                                     20,001            9,528.69     190,583.27

Glumetza                                     7,873            2,048.88      16,130.82

Granisetron HCl                             43,149              180.47       7,787.08

H.P. Acthar                                  3,278           44,101.85     144,565.87 Harvoni                                     78,467           27,720.64   2,175,155.84

Herceptin                                   53,136            3,290.87     174,863.75

Humalog                                    941,420              377.72     355,593.19

Humira                                     219,266            3,673.43     805,458.62

Hydroxychloroquine Sulfate                 545,452              110.00      60,001.01

Invega                                     526,070            1,380.61     726,297.32

Isentress                                  188,181            1,229.77     231,419.27 Lantus                                   3,651,839              393.11   1,435,574.72

Latuda                                     715,975              881.91     631,424.75

Lyrica                                   1,356,527              370.87     503,093.90

Mestinon                                     7,268            1,070.04       7,777.04

Methylphenidate ER                       3,576,101              195.86     700,422.21

Morphine Sulfate                           662,978               62.43      41,389.73

Naproxen Sodium                            370,485               27.33      10,126.81

Neulasta                                    75,594            3,729.84     281,953.81

Norditropin Flexpro                         79,156            3,473.33     274,934.63

Novoseven RT                                 4,444           67,098.11     298,184.00

Phenergan                                   10,047              255.73       2,569.27

Prezista                                   265,823            1,259.27     334,742.62

Proair HFA                               6,690,081               58.56     391,742.23

Proctosol-HC                               146,493               49.12       7,195.57

Pulmozyme                                   66,738            3,356.32     223,994.30

Quelicin                                    29,416              223.57       6,576.41

Remicade                                    52,764            3,576.20     188,694.62 Retin-A Micro                                1,667            1,953.85       3,257.07

Revlimid                                    14,475            9,954.78     144,095.51

Reyataz                                    178,383            1,303.60     232,540.89

Sabril                                      13,297            9,962.99     132,477.85 Seroquel XR                                743,257              650.00     483,117.34

Sovaldi                                     27,228           22,713.59     618,445.60

Spiriva                                  1,255,363              324.15     406,925.46

Stribild                                   176,445            2,580.10     455,245.06

Suboxone                                 2,051,871              233.41     478,918.14

Symbicort                                1,682,405              270.45     455,006.23

Synagis                                    100,034            2,338.19     233,898.45

Tecfidera                                   39,697            5,505.27     218,542.81

Tivicay                                    132,094            1,457.12     192,476.94

Triumeq                                     81,914            2,422.67     198,450.69

Truvada                                    527,386            1,396.28     736,377.75 Ventolin HFA                             7,227,336               49.25     355,949.41

Viekira Pak                                  8,612           24,413.83     210,251.89

Vyvanse                                  3,496,935              223.81     782,651.74

Xifaxan                                     93,982            1,441.23     135,449.72 Xolair                                      55,631            2,501.20     139,144.34

Do you want to plot the top 10 values (yes/no)? no

Enter a year to process (‘q’ to terminate): 2012

Drug spending by Medicaid in 2012

Medication                           Prescriptions   Prescription Cost          Total

Abilify                                  2,934,565              642.71   1,886,082.01

Adderall XR                              1,511,503              243.27     367,706.53

Advair Diskus                            2,359,382              251.29     592,900.57

Advate                                       7,514           21,674.67     162,863.51 Anucort-HC                                   4,186               21.75          91.04

Ativan                                      19,385              147.53       2,859.96

Atripla                                    280,155            1,789.12     501,231.12

Avastin                                     93,763            1,506.96     141,296.63

Carbamazepine                              617,133               17.96      11,084.27

Clindamycin Phos-Benzoyl Perox               3,149              149.21         469.86

Clobetasol Propionate                      448,435               33.37      14,965.04

Complera                                    39,684            1,877.01      74,487.19 Copaxone                                    51,778            4,052.88     209,850.07

Daraprim                                     3,944              482.90       1,904.57

Demerol                                     64,621               24.61       1,590.54 Econazole Nitrate                          170,593               23.28       3,971.12

Enbrel                                     104,737            2,120.79     222,125.19

Epitol                                      40,968                6.75         276.57

Epzicom                                    121,222              979.45     118,730.83

Fentanyl Citrate                           285,140               55.18      15,733.57

Flovent HFA                              2,071,046              148.45     307,448.30

Gleevec                                     16,077            5,910.02      95,015.38

Glumetza                                     6,226              371.46       2,312.70

Granisetron HCl                             37,292               63.47       2,367.08

H.P. Acthar                                  1,303           44,059.63      57,409.70 Herceptin                                   51,709            2,407.18     124,472.77

Humalog                                    626,575              231.68     145,165.13

Humira                                     114,272            2,323.64     265,527.47

Hydroxychloroquine Sulfate                 348,418               13.86       4,827.38

Invega                                     406,323              907.23     368,629.81 Isentress                                  195,434            1,031.31     201,553.62

Lantus                                   2,517,919              211.79     533,281.27

Latuda                                     160,905              514.19      82,735.78

Lyrica                                   1,019,589              211.20     215,339.53

Mestinon                                     8,367              189.46       1,585.18

Methylphenidate ER                       2,932,089              168.52     494,115.10

Morphine Sulfate                           524,402               35.99      18,874.21

Naproxen Sodium                            340,547               10.55       3,594.08

Neulasta                                    74,648            2,998.11     223,802.72

Norditropin Flexpro                         32,740            2,769.43      90,671.08

Novoseven RT                                 3,804           56,437.66     214,688.85 Phenergan                                   11,335               17.52         198.57

Prezista                                   200,271            1,032.74     206,827.56

Proair HFA                               5,455,972               49.57     270,467.51 Proctosol-HC                                89,636                9.58         858.33

Pulmozyme                                   63,223            2,595.71     164,108.80

Quelicin                                    22,282               53.63       1,194.87

Remicade                                    42,291            2,889.87     122,215.65 Retin-A Micro                               39,562              258.50      10,226.79

Revlimid                                     9,249            8,498.63      78,603.81

Reyataz                                    256,659            1,003.84     257,643.89

Sabril                                       8,972            4,663.81      41,843.68

Seroquel XR                                887,711              460.66     408,935.89

Spiriva                                  1,047,429              256.28     268,436.97

Stribild                                     2,520            2,381.47       6,001.31

Suboxone                                 1,407,720              278.23     391,667.33

Symbicort                                  698,988              219.94     153,732.12

Synagis                                    185,864            2,151.77     399,936.52

Truvada                                    470,894            1,175.92     553,732.04 Ventolin HFA                             5,123,890               42.73     218,962.67

Vyvanse                                  2,889,840              165.16     477,289.95

Xifaxan                                     52,056            1,065.21      55,450.67 Xolair                                      36,764            2,167.00      79,667.51

Do you want to plot the top 10 values (yes/no)? no

Enter a year to process (‘q’ to terminate): q

<strong>Test Case 3 – Plot Test (Not on Mimir): </strong>

Input a file name: medicaid_spending.csv

Medicaid drug spending 2011 – 2015

Enter a year to process (‘q’ to terminate): 2013

Drug spending by Medicaid in 2013

Medication                           Prescriptions   Prescription Cost          Total

Abilify                                  2,749,155              731.64   2,011,387.68

Adderall XR                              1,519,701              248.41     377,512.24

Advair Diskus                            2,077,435              279.31     580,242.45

Advate                                      15,337           17,737.43     272,038.97

Anucort-HC                                   4,543               28.94         131.48 Ativan                                      10,861              140.91       1,530.45

Atripla                                    258,157            1,915.29     494,445.97

Avastin                                    103,654            1,399.94     145,109.44

Carbamazepine                              584,314               17.67      10,324.83

Clindamycin Phos-Benzoyl Perox              11,159              144.24       1,609.57

Clobetasol Propionate                      459,091               32.34      14,849.21

Complera                                    73,381            1,959.14     143,763.70

Copaxone                                    47,909            4,582.08     219,523.00

Daraprim                                     3,466              579.98       2,010.21

Demerol                                     57,556               55.21       3,177.66

Econazole Nitrate                          150,475               22.02       3,312.83

Enbrel                                     108,123            2,366.26     255,847.10

Epitol                                      45,149                6.59         297.40

Epzicom                                    118,963            1,032.01     122,771.48

Fentanyl Citrate                           307,787               82.84      25,496.16

Flovent HFA                              2,065,708              161.34     333,273.79

Gleevec                                     16,455            6,588.75     108,417.85

Glumetza                                     1,345              374.93         504.28

Granisetron HCl                             41,572               56.14       2,333.64

H.P. Acthar                                  2,021           41,533.21      83,938.62 Herceptin                                   53,608            2,620.58     140,483.85

Humalog                                    626,112              260.70     163,225.00

Humira                                     127,339            2,613.33     332,779.41

Hydroxychloroquine Sulfate                 373,650               12.61       4,711.37

Invega                                     423,737            1,038.37     439,996.34

Isentress                                  204,795            1,070.59     219,251.61

Lantus                                   2,690,587              252.86     680,347.46

Latuda                                     250,199              626.14     156,660.75

Lyrica                                   1,002,207              246.66     247,204.86

Mestinon                                     8,592              217.22       1,866.40

Methylphenidate ER                       3,456,299              167.39     578,534.69

Morphine Sulfate                           518,903               54.14      28,093.10

Naproxen Sodium                            319,877                9.79       3,132.20

Neulasta                                    72,410            3,107.82     225,037.00

Norditropin Flexpro                         40,357            2,970.33     119,873.51

Novoseven RT                                 3,447           63,685.57     219,524.14

Phenergan                                    9,770               20.86         203.82

Prezista                                   223,170            1,092.12     243,728.80

Proair HFA                               5,404,529               52.91     285,949.65

Proctosol-HC                                87,127               11.49       1,001.15 Pulmozyme                                   64,509            2,764.88     178,359.67

Quelicin                                    22,785               68.93       1,570.62

Remicade                                    42,768            3,022.90     129,283.31 Retin-A Micro                               25,081              417.39      10,468.57

Revlimid                                    10,670            8,842.62      94,350.72

Reyataz                                    228,462            1,100.65     251,457.68

Sabril                                      10,120            6,306.84      63,825.23

Seroquel XR                                751,376              551.57     414,436.25

Sovaldi                                        144           28,167.67       4,056.14

Spiriva                                  1,089,524              278.01     302,903.95

Stribild                                    38,611            2,384.84      92,080.87

Suboxone                                 1,426,840              256.97     366,652.84

Symbicort                                  858,102              234.30     201,057.26

Synagis                                    174,691            2,215.36     387,004.17

Tecfidera                                    7,213            4,534.59      32,708.03

Tivicay                                      2,908            1,322.77       3,846.61

Truvada                                    423,082            1,234.59     522,333.51

Ventolin HFA                             5,331,556               43.73     233,146.29

Vyvanse                                  3,078,059              181.69     559,256.43

Xifaxan                                     60,711            1,141.70      69,313.95 Xolair                                      38,655            2,306.19      89,145.79

Do you want to plot the top 10 values (yes/no)? yes

Enter a year to process (‘q’ to terminate): q




<strong> </strong>

<strong> </strong>

<strong> </strong>





