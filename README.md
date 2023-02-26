# YTDost


## Introduction
 
This is a Python script for a Flask application that summarizes a YouTube video and performs question-answering on a document uploaded by a user. It uses several third-party libraries including googleapiclient, youtube_transcript_api, pytube, transformers, flask, haystack, and werkzeug. The script allows the user to submit a YouTube video URL and generates a summary of the video. It also allows the user to upload a text document and submit a query for the script to search and find the answer to the question.


## Installation

To use this application, you need to have Python 3 installed on your computer. You can then install the required Python packages using pip. To do this, navigate to the directory containing the script and run the following command:

pip install -r requirements.txt

This will install all the required packages listed in the requirements.txt file.


## Usage

To run the application, navigate to the directory containing the script and run the following command:

python app.py

This will start the Flask server and you can access the application by opening a web browser and navigating to http://localhost:5002/.

The application has two endpoints:

    /summarize: This endpoint accepts a GET request and expects a url parameter containing the URL of the YouTube video to summarize. The script first downloads the video, retrieves the captions using the YouTube Data API, and extracts the transcript text using the YouTube Transcript API. It then generates a summary of the transcript text using a pre-trained Hugging Face model for text generation. The summary is returned as a JSON object.

    /predict: This endpoint accepts a POST request and expects a file upload and a query parameter containing the question to be answered. The script first indexes the uploaded document using the Haystack library, and then ranks the documents using the BM25Retriever. It uses the FARMReader to find the answer to the query, and then uses the ExtractiveQAPipeline to extract the answer from the document. The top 10 documents and top 5 passages for each document are returned as a JSON object.

## Configuration

The application requires an API key for the YouTube Data API, which should be specified in the summarize function. You should replace the string <API-KEY> with your actual API key.

The script assumes that the UPLOAD_PATH directory exists and has write permission. If you need to change the directory where uploaded files are saved, you can modify the UPLOAD_PATH variable in the script.

The allowed file types for uploading can be modified by changing the UPLOAD_EXTENSIONS variable in the script.


## Conclusion

This script provides an example of how to use several third-party libraries to build a Flask application for summarizing YouTube videos and performing question-answering on uploaded documents. It can be modified and extended for use in other applications.
