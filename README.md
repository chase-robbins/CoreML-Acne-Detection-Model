# Acne Classifier

## Project Overview

Acne Classifier is an image classification model designed to distinguish between images of skin with acne and clear skin. This project uses machine learning techniques to analyze and categorize skin images, potentially aiding in dermatological assessments or skincare applications.

## Technical Details

- **Author**: Chase Robbins
- **Created Date**: January 16, 2021
- **Model Type**: Image Classifier
- **Framework**: Create ML
- **Version**: 1.1

## Model Specifications

The core of this project is an image classification model with the following characteristics:

- **Input**: Color images (299 x 299 pixels, BGR color space)
- **Output**:
  - Class label ("Acne" or "Clear Skin")
  - Probability for each class
- **Model Architecture**:
  - Vision Feature Print
  - GLM Classifier

## System Requirements

The model is compatible with the following operating systems:

- macOS 10.14+
- iOS 12.0+
- tvOS 12.0+
- macCatalyst 12.0+

## Project Structure

The project consists of the following main components:

1. Machine Learning Model (`.mlmodelc`)
2. Training Data
   - Acne images
   - Clear Skin images
3. Create ML Project file (`.mlproj`)

## Getting Started

To get the Acne Classifier up and running, follow these steps:

1. **Clone the Repository**

   ```
   git clone https://github.com/chase-robbins/CoreML-Acne-Detection-Model.git
   cd acne-classifier
   ```

2. **Install Dependencies**

   - Ensure you have Xcode installed on your Mac (version 10.1 or later).
   - This project uses Create ML, which is included with Xcode.

3. **Open the Project**

   - Open Xcode and select "Open a project or file"
   - Navigate to the cloned repository and open the `.xcodeproj` file.

4. **Build the Project**

   - In Xcode, select your target device (iOS device or simulator).
   - Click the "Build" button (play icon) or use the keyboard shortcut `Cmd + R`.

5. **Use the Model**

   - The `.mlmodelc` file should now be integrated into your Xcode project.
   - You can use the model in your Swift code as follows:

   ```swift
   import Vision

   guard let model = try? VNCoreMLModel(for: AcneClassifier().model) else {
       fatalError("Failed to load Core ML model")
   }

   let request = VNCoreMLRequest(model: model) { request, error in
       guard let results = request.results as? [VNClassificationObservation] else {
           fatalError("Failed to process image")
       }

       // Handle the classification results
       let topResult = results.first
       print("Classification: \(topResult?.identifier ?? "Unknown"), Confidence: \(topResult?.confidence ?? 0)")
   }

   // Use this request with a VNImageRequestHandler to classify images
   ```

6. **Test the Model**
   - You can test the model using the sample images provided in the `Training Data` directory.
   - Implement a user interface to allow image input and display classification results.

## Usage

To use this model in your own application:

1. Load the `.mlmodelc` file into your iOS, macOS, or tvOS application.
2. Prepare an input image of size 299x299 pixels.
3. Use the `predict` method to classify the image.
4. The model will return the most likely class label and probabilities for each class.

## Training Data

The model was trained on a dataset of images categorized into two classes:

1. Acne
2. Clear Skin

Some sample images are included in the `Training Data` directory.

## Future Improvements

- Expand the training dataset for improved accuracy
- Fine-tune the model for better performance
- Add more granular classifications (e.g., different types of acne)

## License

This project is licensed under the MIT License. This means you are free to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the software, subject to the following conditions:

1. The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

2. THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.

## Acknowledgements

This project was created using Apple's Create ML tool (version 2.0).
