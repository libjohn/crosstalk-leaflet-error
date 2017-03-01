# crosstalk-leaflet-error
On Windows I cannot get leaflet to work properly with crosstalk and DT.


## Procedures I ran to determine the problem

### Trial 1
1. run-all leaflet.Rmd
2. knit
3. run flex-empty.Rmd
4. Knit
5. run flex-1a.Rmd
6. Knit
7. crosstalk-1.Rmd   # does not load crosstalk, yet!
8. Knit
9. run crosstalk-2Rmd  # this one does load the crosstalk library but does not run the "share-talk" chunk

- Trial one, if I install.package("leaflet") it installs a two versions of leaflet (1.0.1 & 1.1.0).  

- But I don't have the permissions on this Lab computer to uninstall version 1.0.1.  I'm going to try a VCL.


#### Versions

- $version.string
[1] "R version 3.3.2 (2016-10-31)"
- Rstudio 1.0.44
- crosstalk 1.0.0
- leaflet 1.0.1
- DT 0.2
- Tidyverse 1.0.0
- flexdashboard 0.4

---

### Trail Two

#### RStudio - 1.0.136
- R - R version 3.3.1 (2016-06-21) 
- Tidyverse 1.1.1
- leaflet 1.1.0
- crosstalk 1.0.0

1. run-all leaflet.Rmd
2. knit
    - OUTCOME:  Does not display leaflet basemap in Chrome
    - devtools::install_github("rstudio/leaflet")
    - leaflet 1.1.0.90000
    - OUTCOME: does not work
    - **devtools::install_version("leaflet", version = "1.0.1", repos = "http://cran.us.r-project.org")**
    - ** works again!!**

3. crossralk-1.Rmd
    - install.packages("DT")  # DT_0.2
    - **works fine**

4. crosstalk-2.Rmd
    - OUTCOME: chunk "share-talk" throws error:  Error in pointData.default(data) : Don't know how to get location data from object of class SharedData

    - solution:  devtools::install_github("rstudio/crosstalk")  # version 1.0.1
    - same error

    - switch order of the function calls:
        - from -- leaflet()
            - datatable()
        - to --   datatable()
            - leaflet()

5. different error

- devtools::install_github("rstudio/DT")

- This fixed the datable() error    BUT there is still an error a leaflet

- install.package("leaflet") to 1.1.0
    - ran in rstudio editor
    - knit
    - works in rstudio web-browser
    - same map drawing problem in Chrome


- devtools::install_github("rstudio/leaflet")
    - still doesn't work in Windows Chrome
  





