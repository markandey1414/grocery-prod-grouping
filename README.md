## Product grouping using YOLOv5

Pre-requisite: Python >= 3.10 will work fine, git bash for terminal and `source` commands.

To setup the work environment, run the following commands in order:

> `python -m venv venv`
> `source venv/Scripts/activate`
> `pip install -r requirements.txt`

This creates a virtual environment of the commands that help run the program.

To run the project:
> `python app.py`
The project runs on local port 5000.

GET method runs the detection code on the input image. Image can be a jpeg or a png. Output image is also in the same format. Co-ordinates and confidence score is in json.

The code renders a basic html template `index.html` by POST method as a web page for flask server that runs in the following way:
1. Takes input as an image
2. Runs grocery object detection
3. Outputs the resultant image visualisation
4. Returns the center co-ordinates of the images a json in browser itself

Following changes can be made:
1. Products can be grouped together based on more detailed image processing. When grouping products we have 2 factors in mind, dimensions and color grading.
2. The json output can be saved in a separate file instead of return it raw on the web page.

Instead of grouping the products together using DBScan, they are currently only labeled based on their co-ordinates as weren't able to classify under similar classes. Labeling initially is only intended to be used when classes have been identified. But so is not the case here, hence the co-ordinate based labeling.

The model used here `best.py` is a YOLOv5 fine-tuned model on SKU-110K dataset that is exclusively used for grocery product detection and be downloaded from <a href="https://drive.google.com/file/d/1iq93lCdhaPUN0fWbLieMtzfB1850pKwd">here</a>.


P.S. Instead of Flask, a more intuitive Streamlit page can also be designed for the same because of it's UI and features htat are far more useful for any ML task.
