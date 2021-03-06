# Fake_Job_Prediction using different data mining techniques
Employment scams are on the rise. According to CNBC, the number of employment scams doubled in 2018 as compared to 2017. The current market situation has led to high unemployment. Economic stress and the impact of the coronavirus have significantly reduced job availability and the loss of jobs for many individuals. A case like this presents an appropriate opportunity for scammers. Many people are falling prey to these scammers using the desperation that is caused by an unprecedented incident. Most scammer do this to get personal information from the person they are scamming. Personal information can contain address, bank account details, social security number etc. I am a university student, and I have received several such scam emails. The scammers provide users with a very lucrative job opportunity and later ask for money in return. Or they require investment from the job seeker with the promise of a job. This is a dangerous problem that can be addressed through Machine Learning techniques.

This project uses data provided from Kaggle. This data contains features that define a job posting. These job postings are categorized as either real or fake. Fake job postings are a very small fraction of this dataset. That is as excepted. We do not expect a lot of fake jobs postings. This project follows five stages. The five stages adopted for this project are –

    1.Problem Definition (Problem Statement and Metrics),
    2.Data Collection
    3.Data cleaning, exploring, pre-processing, and Text mining
    4.Modeling with categorical/numeric and text features
    5.Evaluating

<img width="852" alt="stages-of-development" src="https://user-images.githubusercontent.com/54286216/153758402-92428b85-9443-4e21-9753-5e34659cb52e.png">


# Problem Statement
This project aims to create a classifier that will have the capability to identify fake and real jobs. The final result will be evaluated based on the general machine learning different models. The dataset contains 3 different types of data, Numeric, Categorical and Textual. We will be proceeding with two different ways. One with considering all the numeric and categorical features to find result. Another with combining all the textual features(complete text not even categorical). The final models from these two segment will take in any relevant job posting data and produce a final result determining whether the job is real or not.

# Metrics
The models will be evaluated based on two metrics:
     
     1. Accuracy: This metric is defined by this formula -
     
   ![accuracy](https://user-images.githubusercontent.com/54286216/164974127-8964736e-4a50-473a-b6bb-984c2117229d.jpg)
   
   As the formula suggests, this metric produces a ratio of all correctly categorized data points to all data points. This is particularly useful since we are trying to identify both real and fake jobs unlike a scenario where only one category is important.
   
  
     2. F1-Score: F1 score is a measure of a model’s accuracy on a dataset. The formula for this metric is –
     
   ![f1-score](https://user-images.githubusercontent.com/54286216/164974281-a2fb4710-c8e4-4a6e-8e3c-f8950be10b0a.jpg)
   
   F1-score is used because in this scenario both false negatives and false positives are crucial. This model needs to identify both categories with the highest possible score since both have high costs associated to it.
   
   

# Data Explore & Visualization

Dataset used - https://www.kaggle.com/shivamb/real-or-fake-fake-jobposting-prediction

The dataset consists of 17,880 observations and 18 features. The data is combination of integer, binary and textual datatypes. A brief definition of the variables is given below:


![Annotation 2022-04-24 173449](https://user-images.githubusercontent.com/54286216/164974566-6b4bdddc-56b6-42e9-9296-d54eeccd5872.png)
![1dataset](https://user-images.githubusercontent.com/54286216/164974611-dde7e979-6a99-4e83-9e18-199eda349abc.JPG)

Since most of the datatypes are either Booleans or text a summary statistic is not needed here. The only integer is job_id which is not relevant for this analysis.

Numbers of fraudlent job:

![2fraudulent](https://user-images.githubusercontent.com/54286216/165032407-a6abfdea-6669-4b44-9ba9-65660b3d5ca5.JPG)

Numbers of job posted function wise:

![3jobs_function_wise](https://user-images.githubusercontent.com/54286216/165032592-31972b67-ad7c-4bf8-b7c5-6681b9836c87.png)

Numbers of job posted industry wise:

![4jobs_industry2](https://user-images.githubusercontent.com/54286216/165032669-46b360cc-eafd-4af7-a572-085be1ab02f5.png)


Numbers of job posted based on required_education:

![5jobs_required_education](https://user-images.githubusercontent.com/54286216/165032756-d655c78a-3365-42c7-8735-aa38c780c49a.JPG)


Numbers of job posted based on required_experience:

![6jobs_required_experience](https://user-images.githubusercontent.com/54286216/165032850-fdf823c2-c5a2-415f-8484-10a1499223d4.JPG)


Numbers of job posted based on employment_type:

![7jobs_employment_type](https://user-images.githubusercontent.com/54286216/165032930-4c37abb4-00f5-450a-9ce1-6b1e5a3bf42d.JPG)


Numbers of job posted based on telecommunicating, has_company_logo, has_questions:

![8jobs_telcom_logo_questions](https://user-images.githubusercontent.com/54286216/165033292-22e9b905-dd7f-4db1-ac9e-d65e9e086a32.png)


Numbers of job posted based on title:

![9jobs_title](https://user-images.githubusercontent.com/54286216/165033399-c5106bec-0d2c-434c-8aaa-d505e7198dca.png)


Numbers of job posted based on location:

![10jobs_location](https://user-images.githubusercontent.com/54286216/165033457-4fff5087-376c-4a2c-ba50-5d9710865e87.png)


Numbers of job posted department wise:

![11jobs_department](https://user-images.githubusercontent.com/54286216/165033527-56a01ab6-bb04-4f0d-bb4b-d216ecfdffd2.png)


****Visualization of integer/numeric features

![17](https://user-images.githubusercontent.com/54286216/165063258-7b575cd6-ad0b-41e2-98b2-3a7373afe74e.JPG)


****Visualization of text fields/columns

![12jobs_text](https://user-images.githubusercontent.com/54286216/165034233-31908927-bc0d-4cf5-b145-2ed83f90f5d9.JPG)

 Features like company_profile, description, requirements and benefits are complete text- Textual Datasets


****Checking numbers of missing/null values of the fields

![14jobs_nullvalues](https://user-images.githubusercontent.com/54286216/165034863-4e3187ca-cf0c-4f93-ab15-8ac92061f892.JPG)

There are lot of missing values which has to be handled later.

****Correlation Matrix: to study the relationship between the numeric data.

![13jobs_correlation](https://user-images.githubusercontent.com/54286216/165035573-9a1b8c81-4d97-4026-9f53-c5756d94788a.png)

Here telecommuting has no correlation, as a result it can be excluded. The other has slight negative correlation. 



# Data Cleaning
    ****Categorical,Numeric features
    
   1.Removed the irrelevent and the features which holds more than 60% missing values:- job_id(irrelevant), salary_range and department has lots of missing values almost 70% out of 17880 instances.
   
   2.Removing telecommuting feature too as it has no corelation
   
   3.Handling missing/null values- replacing the categorical features with the most appeared values
   ![Annotation 2022-04-25 152746](https://user-images.githubusercontent.com/54286216/165062239-d0741276-bf21-427a-81b0-44526357057f.png)
   ![16jobs_cleaned](https://user-images.githubusercontent.com/54286216/165062634-2c82535b-2b48-434c-bb7e-307ae67c5b6e.JPG)
   
   4.Dropped the duplicate records
   
   5.Converted categorical features to numeric by label encoder
   
   6.Dataset was highly imbalanced, as a result balanced out the data by oversampling method(SMOTETomek)
   
   Cleaned Data
   
   ![15jobs_processed](https://user-images.githubusercontent.com/54286216/165064125-8d796940-1140-47ff-80de-ce3de04b62ec.JPG)

  
  
    
    ****Text Minning from textual fields
    
   
   1. Extracted and concatenated all the text fields.
   
   2. Natural Language Processing (NLTK, Spacy) 
   
   3. Created a wordcloud(most appeared words)
          
        WordCloud Real
           
         ![real](https://user-images.githubusercontent.com/54286216/168412685-a0ec805b-6ee8-418b-be10-099dbb8dc077.png)

        WordCloud Fraud
        
         ![fraud](https://user-images.githubusercontent.com/54286216/168412711-0f848ddb-deef-48ab-b427-3a82d7743fd3.png)

   4. 
   
   ![nlp](https://user-images.githubusercontent.com/54286216/168413304-004f503a-11bf-445f-b522-9e3731f01070.png)

   Tokenization: The textual data is split into smaller units. In this case the data is split into words.

   To Lower: The split words are converted to lowercase
   
   Stopword removal: Stopwords are words that do not add much meaning to sentences. For example: the, a, an, he, have etc. These words are removed.

   Stemming: Stemming identifies the common root form of a word by removing or replacing word suffixes (e.g. “flooding” is stemmed as “flood”)

   5. Text mining/ Text feature extracton using TfidfVectorizer.


# Results and Findings

Model evaluations with Categorical Features

![results categr](https://user-images.githubusercontent.com/54286216/168414065-eb791776-0aa9-4c28-8ea5-d4c9592414f8.png)

Here best model that performs is Random Forest classifier, whereas Support Vector machine performs poorly.

Model evaluations with Text Features

![results text](https://user-images.githubusercontent.com/54286216/168414103-2babb935-30a5-48f3-8189-6e380becffe7.png)

Here best model that performs is Support Vector Machine. But in general all the other model performs better with text mining than categorical data excluding K-nearest neighbour. KNN is the least best model that performs.

***Confusion Matrix for best models from each approach

Random Forest   ...................................................................    Support Vector Machine

![21randomforest](https://user-images.githubusercontent.com/54286216/168414313-2a4c4a07-81ab-4660-a2c9-4fc5ddbb065f.JPG)
![2](https://user-images.githubusercontent.com/54286216/168414329-4d914c75-4e97-46db-b1f1-53df06a25431.png)


Combined Model evaluation plots

![bar-graph (1)](https://user-images.githubusercontent.com/54286216/168415386-e1d76ee5-686d-4475-8fb0-a5e2c9a8d52a.png)
![bar-graph (2)](https://user-images.githubusercontent.com/54286216/168415394-d3a50daa-b522-42a5-93d9-e1ac9f4e6115.png)


