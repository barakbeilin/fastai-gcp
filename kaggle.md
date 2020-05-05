 --------- Installing Kaggle   ---------

 1. run `pip install kaggle` (the conda envrinoment with fastai is the `base`).
 2. Add an API TOKEN on the `kaggle.com` site.
 3. Download the token `kaggle.json` file to the gcp machine (I used the chrome sheel which has a gui for upload).
 4. In the GCP shell:
    a. I had something stragne with the `~/.kaggle` directory so I deleted it and made a new one.
    b. I moved the `kaggle.json` file to the destination `/home/t/.kaggle/kaggle.json`
    c. I tried to run `kaggle` command with no flags, but was asked to run `chmod 600 /home/t/.kaggle/kaggle.json`, I did it.



--------- Setting a GCP bucket  ---------
1. Followed instruction[`https://www.kaggle.com/c/rsna-intracranial-hemorrhage-detection/discussion/111029`]
2. mount bucket to GCP instance `gcsfuse my-fastai-instance-bucket /mnt/buckets/`  ()
3. copy file from engine to bucket: `gsutil cp herbarium-2020-fgvc7.zip gs://my-fastai-instance-bucket`


--------- Dataset manipulation  ---------
1. unzipping dataset`unzip herbarium-2020-fgvc7.zip`

