

# Estimating the effect of the amount of comments on 

Custom lexicons about suicidal thoughts and behaviors (STBs) are within `create_dataset.ipynb`

`download_reddit_posts_and_comments.ipynb`

* Takes SuicideWatch (SW) posts from 2018 and 2019 from Reddit Mental Health Dataset, looks for posts from the same authors, then looks for comments for every SuicideWatch post (an author may have several SW posts, not contained in the Reddit Mental Health Dataset). 
* Data cleaning: remove deleted ("[deleted]") authors and posts and "[removed]" posts. Deleted = was deleted by submission user; removed = removed by moderator for violating subreddit rules such as being offensive or possibly a trivia rules

* input
    * `suicidewatch_2018_features_tfidf_256.csv`
    * `suicidewatch_2019_features_tfidf_256.csv`
* output:  
    * `./input/all_submissions_2021-07-20-23-11-56.csv` sorted first by user then created_utc (oldest to newest)
    * `./input/first_sw_submission_2021-07-20-23-12-27.csv` 
    * `./input/first_sw_comments_2021-07-20-18-52-35.csv` 




`create_dataset.ipynb` 
* Combine 'title' and 'selftext' col and input to to LIWC 2015 and output `first_sw_submission_liwc2015_2021-07-20-23-12-27.csv`
* Takes post df and comments df from `download_reddit_posts_and_comments.ipynb` and finds first suicidal post, counts distribution of subsequent posts, and adds comments. Dropped rows from `first_sw_submission_2021-07-20-23-12-27.csv` that had `NaN` in `created_utc`.

* Feature extraction
* input: 
    * outputs of `download_reddit_posts_and_comments.ipynb`:
        * `./input/all_submissions_2021-07-20-23-11-56.csv` sorted first by user then created_utc (oldest to newest)
        * `./input/first_sw_submission_2021-07-20-23-12-27.csv` 
    
* output:
  * `first_sw_submission_liwc2015_subsequent_posts_lexicons_2021-07-20-23-12-27.csv` 


`psm.ipynb`
* Propensity Score Matching analysis using `DoWhy` package.
* input
    * `first_sw_posts_2021-04-17-20-27-30.csv`
    `first_sw_submission_liwc2015_subsequent_posts_lexicons_2021-07-20-23-12-27.csv`
* output
    * figures and tables in manuscript


