import cv2
import imutils
import argparse

# Initialize HOG descriptor
HOGCV = cv2.HOGDescriptor()
HOGCV.setSVMDetector(cv2.HOGDescriptor_getDefaultPeopleDetector())


def detect(frame):
    # Detect bounding boxes for people in the frame
    bounding_boxes, weights = HOGCV.detectMultiScale(frame, winStride=(4, 4), padding=(8, 8), scale=1.03)

    # Draw bounding boxes and labels on the frame
    person = 1
    for x, y, w, h in bounding_boxes:
        cv2.rectangle(frame, (x, y), (x + w, y + h), (0, 255, 0), 2)
        cv2.putText(frame, f'person {person}', (x, y), cv2.FONT_HERSHEY_SIMPLEX, 0.5, (0, 0, 255), 1)
        person += 1

    # Display the processed frame
    cv2.imshow('output', frame)
    return frame


def detect_by_video(video_path):
    # Open the video file
    video = cv2.VideoCapture(video_path)

    # Process each frame
def detect_by_video(video_path):
    # Open the video file
    video = cv2.VideoCapture(video_path)
    check, frame = video.read()
    if check == False:
        print("Video not found! Please check video path...")
        return

    # Process each frame
    while video.isOpened():
        # Read the next frame
        check, frame = video.read()

        if check:
            # Resize the frame and detect people
            frame = imutils.resize(frame, width=min(800, frame.shape[1]))
            frame = detect(frame)

            # Wait for key press to stop processing
            key = cv2.waitKey(1)
            if key == ord('q'):
                break
        else:
            break

    # Release the video file and close all windows
    video.release()
    cv2.destroyAllWindows()

def detect_by_camera():
    # Open the webcam
    video = cv2.VideoCapture(0)

    # Process each frame
    while True:
        # Read the next frame
        check, frame = video.read()

        # Detect people
        frame = detect(frame)

        # Wait for key press to stop processing
        key = cv2.waitKey(1)
        if key == ord('q'):
            break

    # Release the webcam and close all windows
    video.release()
    cv2.destroyAllWindows()

def detect_by_image(image_path, output_path=None):
    # Read the image file
    image = cv2.imread(image_path)

    # Resize the image and detect people
    image = imutils.resize(image, width=min(800, image.shape[1]))
    result_image = detect(image)

    # Save the processed image to file (if specified)
    if output_path is not None:
        cv2.imwrite(output_path, result_image)

    # Wait for key press to close window
    cv2.waitKey(0)
    cv2.destroyAllWindows()

def main():
    # Parse command line arguments
    parser = argparse.ArgumentParser()
    parser.add_argument("-v", "--video", default=None, help="path to video file")
    parser.add_argument("-i", "--image", default=None, help="path to image file")
    parser.add_argument("-c", "--camera", action="store_true", help="use camera as input")
    parser.add_argument("-o", "--output", default=None, help="path to output file")
    args = parser.parse_args()

    # Detect people in the specified input
    if args.video is not None:
        detect_by_video(args.video)
    elif args.camera:
        detect_by_camera()
    elif args.image is not None:
        detect_by_image(args.image, args.output)

if __name__ == "__main__":
    main()
