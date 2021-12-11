# indigenous_vs_non_indigenous_sentence_length_differences

Project name: Statistical significance of indigenous vs non-indigenous racial grouping as a factor in determining aggregated sentence length in Canada?

-   authors: Chaoran Wang, Rada Rudyak, Kyle Ahn, Mukund Iyer

## Project Summary

For this project we have carried out a hypothesis test to determine if there was a significant difference in the median sentence lengths between the indigenous and non-indigenous offenders under the Correction Services Canada. The median was selected as the measure of central tendency and a permutation test under the null model was carried out computationally with a significance level of **0.05**.

The null hypothesis stated that there was no difference in the population medians in sentence length between indigenous and non-indigenous offenders. The alternate hypothesis stated that there is a difference in the population medians in sentence length between indigenous and non-indigenous offenders. At the EDA stage, we presented two visualizations comparing the sentence lengths for both groups: density plot and box plot.

At the hypothesis test, we identified the difference in the two medians of **-56 days**, with a corresponding *p-value* of **0.0328**. The indigenous group was found to have shorter sentence lengths than the non-indigenous group. As this p-value was smaller than the significance level, there was statistically significant evidence to reject the null hypothesis that stated that there is no difference in the median sentence lengths between the two groups. Considering the large sample size, there is a small chance that the result is affected by the Type II error. However, we have to be mindful of the small effect size. This may raise some concern regarding the practical implications of the study, but we believed it was important not to miss any existing effect. We concluded that in our case, minimizing Type II error was more important than Type I error.

In the final report, we included the quantitative results of hypothesis test as well as the visualization of the distribution of differences in means.

The data set used for this study is the Offender Profile from 2017-2018 released by the Correctional Service of Canada. The link to this site can be found [here](https://open.canada.ca/data/en/dataset/844ff1e3-e137-41be-9ebe-6bd9843c1a53). Each entry in the data set corresponds to a single offender serving a two or more year long sentence. The demographic details such as age, gender and marital status at year end are provided for each entry. This was retrieved from the Offender Management System (OMS). For the purposes of our inquiry, we dropped all columns except the racial grouping and the aggregated sentence length.

## Report

The final report, including quantitative analysis and visual figures, can be found [here](https://htmlpreview.github.io/?https://github.com/UBC-MDS/DSCI_522_inference_on_indigenous_vs_non_indigenous_sentence_length_differences/blob/main/doc/sentence_length_diffs_inference_report.html).

## Usage
To replicate the analysis, clone this GitHub repository, ensure you have installed the [dependencies](#dependencies) listed below.
You may choose to replicate the analysis in 3 different ways: Docker, Make or Running Scripts Manually.
Please refer to the documentation below.

### 1. Docker
In this approach, [Docker](https://www.docker.com/get-started) is required to be installed in order to replicate the analysis. Once [Docker](https://www.docker.com/get-started) is installed, clone this repository.

For your convenience all the output files are already incldued. So, to clear all the results and set to a clean state, please run the following command at the root directory of this project

    docker run --rm -it -v <ABSOLUTE_PATH_TO_PROJECT_DIRECTORY>:/home/inference_on_indigenous_vs_non_indigenous_sentence_length_differences kyleahn/inference_on_indigenous_vs_non_indigenous_sentence_length_differences make -C /home/inference_on_indigenous_vs_non_indigenous_sentence_length_differences clean

To replicate the analysis, please run the following command at the root directory of the project. This will create all the output files as well as the final report .html file.

    docker run --rm -it -v <ABSOLUTE_PATH_TO_PROJECT_DIRECTORY>:/home/inference_on_indigenous_vs_non_indigenous_sentence_length_differences kyleahn/inference_on_indigenous_vs_non_indigenous_sentence_length_differences make -C /home/inference_on_indigenous_vs_non_indigenous_sentence_length_differences all

Note: R packages in `Dockerfile` are not specified versions in order to avoid unncessary conflicts between dependencies. This means that different versions of R packages may be installed in Docker image. If you encounter any problems replicating the analysis on Docker, please try the other two approaches as alternatives.
### 2. Make
For your convenience all the output files are already incldued. So, to clear all the results and set to a clean state, please run the following command at the root directory of this project

    make clean

To replicate the analysis, please run the following command at the root directory of the project. This will create all the output files as well as the final report .html file.

    make all

#### Makefile Dependency Diagram 
![](./Makefile.png)


### 3. Running Scripts in Command Line**

To download data:

    python src/download_data.py --url="http://www.csc-scc.gc.ca/005/opendata-donneesouvertes/Open%20Data%20File%2020170409%20v3%20(English).csv" --file_path="../data/raw/offender_profile.csv".csv" --file_path="./data/raw/offender_profile.csv"

Run eda report and save it as PDF in src folder:

    jupyter nbconvert --to pdf --execute "src/eda_offender_profile_raw_data.ipynb"

Run clean_offender_profile_raw_data.r to clean and process the data for EDA and hypothesis testing:

    Rscript src/clean_offender_profile_raw_data.r --raw_data_path="./data/raw/offender_profile.csv" --processed_dir_path="./data/processed"

Run eda on cleaned and processed data:

    python src/eda_processed_data.py --processed_data_path="./data/processed/processed_offender_profile.csv" --results_folder_path="./results"

Run hypothesis test and produce output in the results folder:

    Rscript src/hypothesis_test.r --processed_data_path="./data/processed/processed_offender_profile.csv" --results_dir_path="./results"

Run to generate sentence_length_diffs_inference_report html and md to view:

    Rscript -e "rmarkdown::render('./doc/sentence_length_diffs_inference_report.rmd')"
    

## Dependencies {#dependencies}

-   Python 3.7.3 and Python packages:

    -   docopt==0.6.2
    -   numpy==1.21.2
    -   pandas==1.3.2
    -   altair==4.1.0
    -   altair_saver==0.5.0

-   R version 3.6.1 and R packages:

    -   knitr==1.26
    -   docopt==0.7.1
    -   janitor==2.1.0
    -   tidyverse==1.3.1
    -   testthat==3.0.4
    -   infer==1.1.0
    -   kableExtra==1.3.4

-   GNU make 4.2.1
-   Docker Desktop

## License

The 'Inference on Indigenous and Non-Indigenous Sentence Lengths' materials here are licensed under the MIT License. If re-using/re-mixing please provide attribution and link to this webpage.

# References

Owusu-Bempah, A., Kanters, S., Druyts, E. et al. Years of life lost to incarceration: inequities between Aboriginal and non-Aboriginal Canadians. BMC Public Health 14, 585 (2014). [https://doi.org/10.1186/1471-2458-14-585](https://bmcpublichealth.biomedcentral.com/articles/10.1186/1471-2458-14-585)
