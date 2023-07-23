# Plant Disease Detection System

The Plant Disease Detection System combines a user-friendly Svelte JS frontend with a powerful FastAPI backend using a CNN in TensorFlow. It allows users to upload plant leaf images to determine their health status accurately. This integration aims to aid farmers and researchers in monitoring and safeguarding plant health for sustainable agriculture practices.

The system consists of two parts: a backend developed using FastAPI and Python, and a frontend developed using Svelte JS. The backend uses a Convolutional Neural Network (CNN) 

## What I learned

During the development of the Plant Disease Detection System, several valuable lessons were gained:

- **Deep Learning with CNNs:** Implementing Convolutional Neural Networks (CNNs) in TensorFlow for image classification tasks helped to understand the power of deep learning and its potential in solving real-world problems.

- **Backend Development with FastAPI:** Creating a backend using FastAPI introduced the concept of building robust APIs with Python, enabling seamless communication between the machine learning model and other applications.

- **Data Preprocessing:** Handling and preprocessing image data for training the CNN, including data augmentation techniques, was crucial to improve the model's performance.

- **Virtual Environments:** Utilizing virtual environments with Python (venv) helped manage dependencies effectively and isolate project environments.

- **Model Deployment:** Deploying the trained CNN model as an API allowed us to integrate machine learning into web applications for practical use.

The experience gained from developing the Plant Disease Detection System deepened the understanding of machine learning, API development, and project management, providing valuable skills for future projects in related fields.

## Prerequisites

Here are some related projects

Before proceeding with the installation, make sure you have the following prerequisites installed on your system:

- Python 3.x
- Node.js (v14 or higher)

clone this repo

`https://github.com/Adbspec/Plant_disease_detection.git`

### Backend installation

1. Navigate to Backend directory:
`cd ./api`

2. Create a virtual environment and install dependencies using requirements.txt file:
`py -m venv venv`

3. Activate the venv:
` venv\Scripts\Activate `

4. Install dependencies
`pip install -r requirements.txt`

5. After successfull installation run the fastapi server:
`py main.py`

The backend API will now be running at http://localhost:8000. Keep this terminal running as it will handle incoming requests from the frontend.

### Frontend Installation

1. Navigate to the frontend directory:
`cd ../frontend2.0`

2. Install Node.js dependencies:
`npm install`

3. After successfull installation run the frontend:
`npm run dev`

The frontend will be accessible at http://localhost:3000

## How to use
- Access the frontend using the provided URL.
- Upload an image of a plant leaf that you want to identify as healthy or diseased.
- The frontend will send the image to the backend API, which will process it through the trained CNN model.
- The backend will return the prediction result to the frontend.
- The frontend will display the result, indicating whether the leaf is healthy or diseased.

## Closing the Application
To stop the backend server, go to the terminal where the server is running and press `Ctrl + C`.

To stop the frontend development server, go to the terminal where the server is running and press `Ctrl + C`.

## Contributing
If you'd like to contribute to the app, feel free to submit a pull request with your changes. Please make sure to follow the existing coding style and include tests for any new functionality you add.

 
