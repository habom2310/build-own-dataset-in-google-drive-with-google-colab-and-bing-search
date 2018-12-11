# Build your own dataset in GOOGLE DRIVE with GOOGLE COLAB and BING SEARCH
With the help of cloud storage (GOOGLE DRIVE), cloud computing (GOOGLE COLAB) and search api (BING SEARCH) we can now do so many things without using any physical resource from our computer. It makes developers' lives become more convenient and easier. Today, I would like to introduce a method to use those free available resources to make our own dataset. 

# Step by step 

 1. First, you need to have a Google account. Then go to https://colab.research.google.com/ to set up your workspace. Go to <b>Edit > Notebook settings</b> or <b>Runtime>Change runtime type</b> and select <b>GPU</b> as Hardware accelerator. Google Colab provides free Tesla K80 GPU so why don't use it. 

 2. Run the following command to install needed packages:
 
 ```
 !apt-get update -qq 2>&1 > /dev/null 
 !apt-get install -y -qq software-properties-common python-software-properties module-init-tools
 !add-apt-repository -y ppa:alessandro-strada/ppa 2>&1 > /dev/null
 !apt-get update -qq 2>&1 > /dev/null
 !apt-get -y install -qq google-drive-ocamlfuse fuse
 ```
 
 ![Alt text](https://github.com/habom2310/build-own-dataset-in-google-drive-with-google-colab-and-bing-search/blob/master/images/1.PNG)
 3. Then mount your Google Drive to your workspace:
 
 ```
 from google.colab import drive
 drive.mount('/content/drive')
 ```
 
 ![Alt text](https://github.com/habom2310/build-own-dataset-in-google-drive-with-google-colab-and-bing-search/blob/master/images/2.PNG)
 
 After finish mounting your Google Drive, you can see on the left panel:
 
 ![Alt text](https://github.com/habom2310/build-own-dataset-in-google-drive-with-google-colab-and-bing-search/blob/master/images/5.PNG)

 4. Create a folder in your Google Drive, name it `AI_CODE_LAB` or whatever you want, then run this command:
 
 ```
 import os
 os.chdir("drive/My Drive/AI_CODE_LAB")
 ```
 
![Alt text](https://github.com/habom2310/build-own-dataset-in-google-drive-with-google-colab-and-bing-search/blob/master/images/4.PNG)
 
 now you are in the folder `AI_CODE_LAB` that you've just created.
 
 5. Download the file `make_dataset.py` in this repository and put it inside the folder AI_CODE_LAB in your Google Drive.
 
 ![Alt text](https://github.com/habom2310/build-own-dataset-in-google-drive-with-google-colab-and-bing-search/blob/master/images/6.PNG)
 
 Check if it's there:
 
 ```
 !ls
 ```
 
 ![Alt text](https://github.com/habom2310/build-own-dataset-in-google-drive-with-google-colab-and-bing-search/blob/master/images/8.PNG)
 
 6. Create a Microsoft account to get free 7-day access to [Bing web search api](https://azure.microsoft.com/en-us/services/cognitive-services/bing-web-search-api/). Insert your api key string at line 22 in the file `make_dataset.py`.
 
 7. Create a folder name `dataset` in the folder `AI_CODE_LAB` to store your dataset. Then run:
 
 ```
 !python make_dataset.py -q iphone -o dataset/iphone
 ```
 
 you can replace `iphone` by whatever you need for your dataset.
 
 8. Wait.
 
# Further works
 - For other types of dataset (csv, mp3, words ...) the approach is the same, you just need to have an API for it or you can make your own web scrapping.
 - You also can train your machine learning models in Google Colab with this dataset, enjoy the power of the Tesla K80.
 
# Acknowledgement
- Thanks Google Colab for providing us with free GPU computing.
- Thanks Bing for an amazing search API, but I wish it would be longer than 7 days.
- Thanks to Adrian from Pyimagesearch for the [tutorial of making a dataset with Bing search](https://www.pyimagesearch.com/2018/04/09/how-to-quickly-build-a-deep-learning-image-dataset/)
