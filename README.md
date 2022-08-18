# Data
Data for this programme are available through the EU Open Data Portal, but here I used elements from a version of these data that has already been cleaned and geocoded by Gadár et al (2020). While there are over 4000 HEIs involved in the Erasmus exchange programme,  I limited myself to consider only the subset of ~300 universities for which I have additional information on their academic impact, coming rom the recent paper by Kosztyán et al (2021).
This included things like the Scimago and CWTS Leiden university rankings, both of which used information on journal publications to create a bibliometric measure of each university’s academic impact (primarily using citation networks and centrality measures). From the larger set of HEIs involved in the Erasmus exchange, Kosztyán and colleagues included only those European universities that were also indluded in the Scimago and Leiden rankings.
Here, I employed six files: 

The first file (HEI_metadata.csv) contains information on each of the“higher education institutions.”The variables I explicitly drew upon are as follows: 
•    Erasmus ID: the unique ID code for the university 
•    Region: based on the UN geoscheme,each university is located in Northern, Eastern, Southern, or Western Europe 
•    Latitude and Longitude: the coordinates (in decimal degrees) giving the exact location of the university 
•    2013 Ranking: Scimago’s rank of the university in 2013. 
•    Total academic staff (FTE): the total number of full-time employed staff at each university, which we can take as a rough proxy of the university’s size 
•    POI_count: a count of the “points of interest” that are physically near each university’s campus, such as restaurants, cinemas, hotels, and hospitals), which we can take as a measure of the amenities near the university, and perhaps as a rough proxy of urbanity. 

The remaining files (main_el.csv, hum_el.csv, soc_el.csv, sci_el.csv, and eng_el.csv) are edge dataframes, where the first column represents the sending university, the second column represents the receiving unicersity, and the third column represents the number of students who went from the first to study at the second. All of these third column represents the number of students who went from the first to study at the second. All of these files relate to student exchanges in the 2013-2014 academic year and are limited to only those universities that are included in the Kosztyán et al (2021) dataset. Main_el includes a count of all student exchanges, while the others consider a subset of those, divided out by the academic subject the students were going to study.
•    hum_el considers subjects in Humanities and Arts 
•    soc_el considers subjects in Social sciences, Business and Law 
•    sci_el considers subjects in Science, Mathematics and Computing 
•    eng_el considers subjects in Engineering, Manufacturing and Construction 

I used these files to generate a number of  networks, where nodes are the universities and edges are  the number of studentsfromUniversity A who went to study at University B. 

Specifically, I made the following six networks
•   “main” network: A weighted, directed network based on the main_el file, representing all student exchanges in 2013-2014 between the universities included in the the Kosztyán et al 
•   Four “subject” networks: one from Humanities and Arts (based on hum_el), one for Social sciences, Business and Law (based on soc_el), one for Science, Mathematics and Computing (based on sci_el), and one for Engineering, Manufacturing and Construction (based on eng_el).
•  “reduced” network: The “main” network reduced to only include edges where at least 5 students went from University A to University B, and where any universities who as a result of this removal of edges are isolates are removed.
