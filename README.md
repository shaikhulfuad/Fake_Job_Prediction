# Fake_Job_Prediction using different data mining techniques
Employment scams are on the rise. According to CNBC, the number of employment scams doubled in 2018 as compared to 2017. The current market situation has led to high unemployment. Economic stress and the impact of the coronavirus have significantly reduced job availability and the loss of jobs for many individuals. A case like this presents an appropriate opportunity for scammers. Many people are falling prey to these scammers using the desperation that is caused by an unprecedented incident. Most scammer do this to get personal information from the person they are scamming. Personal information can contain address, bank account details, social security number etc. I am a university student, and I have received several such scam emails. The scammers provide users with a very lucrative job opportunity and later ask for money in return. Or they require investment from the job seeker with the promise of a job. This is a dangerous problem that can be addressed through Machine Learning techniques.

This project uses data provided from Kaggle. This data contains features that define a job posting. These job postings are categorized as either real or fake. Fake job postings are a very small fraction of this dataset. That is as excepted. We do not expect a lot of fake jobs postings. This project follows five stages. The five stages adopted for this project are –

Problem Definition (Problem Statement and Metrics),
Data Collection
Data cleaning, exploring, pre-processing, and Text mining
Modeling with categorical/numeric and text features
Evaluating

<img width="852" alt="stages-of-development" src="https://user-images.githubusercontent.com/54286216/153758402-92428b85-9443-4e21-9753-5e34659cb52e.png">


# Problem Statement
This project aims to create a classifier that will have the capability to identify fake and real jobs. The final result will be evaluated based on the general machine learning different models. The dataset contains 3 different types of data, Numeric, Categorical and Textual. We will be proceeding with two different ways. One with considering all the numeric and categorical features to find result. Another with combining all the textual features(complete text not even categorical) to find result. The final models from these two segment will take in any relevant job posting data and produce a final result determining whether the job is real or not.
