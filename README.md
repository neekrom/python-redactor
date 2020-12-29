# python-redactor

## Description
Running server.py will start a Flask server that accepts POST requests containing a file in jpg, jpeg, png formats at localhost:5000. 

It will return a JSON containing "boxes", an array of multiple arrays each of which contains a starting X coordinate, starting Y coordinate, ending X, and ending Y that corresponds to a bounding box around any text the EAST detection model sees. 

The JSON also contains a "text" array that contains strings corresponding to the same index as the box it describes in the "boxes" array.

## Requirements
* [Tesseract](https://github.com/tesseract-ocr/tesseract)
* Python Packages
  * pytesseract
  * opencv-python
  * Flask
  * numpy
  
To install the python packages, run 
```python
pip install <package name>
```
If you choose to build an image with Docker, then this step is unnecessary as they will be built together.

## Usage With Docker
Tested using the Postman Desktop App

1. After pulling from the repository, navigate to the directory containing Dockerfile and run 
```
docker build .
```
2. After the image is done buildng, run
```
docker run -p 5000:5000 <image ID>
```
which should show the IP the server is hosted on

3. In the Postman Desktop App, setup a new request to the IP above
4. Change the request type to POST
5. Click body in the navigation bar of that request, and click "form-data". 
6. Include a file with the key "file" that is a picture with text of the form jpg, jpeg, or png. It should look something like the picture below
![example request](https://i.imgur.com/T0iCBLI.png)
7. Send the request and you should receive a JSON of the aforementioned format described in the description

## Without Docker
If you choose not to use Docker, install the required packages manually, pull from the repository, run server.py, and continue from Step 3 above.
