# DSCI_522_indigenous_vs_non_indigenous_sentence_length_differences

Project name: Statistical significance of indigenous vs non-indigenous racial grouping as a factor in determining aggregated sentence length in Canada?

  - authors: Chaoran Wang, Rada Rudyak, Kyle Ahn, Mukund Iyer
 
 ## Project Proposal

For this project, we will infer if there is a statistically significant difference in the length of sentences of indigenous and non-indigenous offenders in the Correctional Services of Canada. Having an impartial law system is paramount in any society, and this study will explore any biases in sentencing based on racial grouping. In general, the number of indigenous incarceration has increased by 40% in the prison system over the last decade, a faster rate than any other group (Owusu-Bempah A, Kanters S, Druyts E). It will be important to see if such differences also exist in the length of the sentence. 

The data set used for this study is the Offender Profile from 2017-2018 released by the Correctional Service of Canada. The link to this site can be found [here](https://open.canada.ca/data/en/dataset/844ff1e3-e137-41be-9ebe-6bd9843c1a53). Each entry in the dataset corresponds to a single offender serving a two or more year long sentence. The demographic details such as age, gender and marital status at year end are provided for each entry. This was retrieved from the Offender Management System (OMS).

The inferential question above will be answered using a hypothesis test with a significance level of 0.05. The null hypothesis will state that there is no difference in the population parameter that we choose to test between the indigenous and non-indigenous groups. The alternate hypothesis will state that there is a difference in the population parameter we choose to test between the indigenous and non-indigenous groups. 

Initially, the analysis will involve exploratory data analysis, where we will use tables that summarize the data. This will tell us how many groups there are under the race column and the sample size. If there are more than two groups, we will need to group all the non-indigenous races together. Then, we will view the distribution of the sentence length for either group using a density plot as the shape of the distribution will dictate the test statistic we use and subsequently the flavor of the statistical test. If the distributions follow a normal distribution, and if we have more than 30 samples in each group, then we can test the difference in means using a student's t-test. However, if the distribution is skewed, then we will test the difference in medians using a permutation test under the null hypothesis computationally. The median can be examined as it is less affected by outliers.

The final evaluation will be completed by obtaining the p-value based on the effect size for our samples and comparing it to our significance level. If the p-value is smaller than the significance level, we can claim that there is enough statistical evidence to reject the null hypothesis. The null distribution and test statistic will presented as a figure, and the p-value and effect size in a table. Whilst evaluating our findings, we will need to consider the power of the test based on the sample size and the magnitude of the effect we observed. The preliminary EDA can be found in this [file](https://github.com/UBC-MDS/DSCI_522_inference_on_indigenous_vs_non_indigenous_sentence_length_differences/blob/main/src/EDA.ipynb).

## Report

The final report can be found
[here](Final Report URL).

## Usage

To replicate the analysis, clone this GitHub repository, ensure you have installed the
[dependencies](#dependencies) listed below, and run the following
commands in the command line/terminal from the root directory of this sequentially
project:

    # download data
    python src/download_data.py --url="http://www.csc-scc.gc.ca/005/opendata-donneesouvertes/Open%20Data%20File%2020170409%20v3%20(English).csv" --file_path="../data/raw/offender_profile.csv".csv" --file_path="./data/raw/offender_profile.csv"
    
    # run eda report and save it as PDF in src folder
    jupyter nbconvert --to pdf --execute "src/eda_offender_profile_raw_data.ipynb"

    # run sample-docopt.R (To be removed)
    Rscript src/sample-docopt.r --raw_data_path="./data/raw/offender_profile.csv" --processed_dir_path="./data/processed"

## Dependencies

  - Python 3.7.3 and Python packages:
      - docopt==0.6.2
      - numpy==1.21.2
      - pandas==1.3.2
      - altair==4.1.0
      - altair-saver==0.5.0
  - R version 3.6.1 and R packages:
      - knitr==1.26
      - docopt==0.7.1

## License

The Breast Cancer Predictor materials here are licensed under the MIT License. If re-using/re-mixing please provide attribution and link to this webpage.

# References 

Owusu-Bempah, A., Kanters, S., Druyts, E. et al. Years of life lost to incarceration: inequities between Aboriginal and non-Aboriginal Canadians. BMC Public Health 14, 585 (2014). [https://doi.org/10.1186/1471-2458-14-585](https://bmcpublichealth.biomedcentral.com/articles/10.1186/1471-2458-14-585)

