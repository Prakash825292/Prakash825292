import cv2
import numpy as np

# Load the image
image = cv2.imread('image_with_emoji.jpg')

# Create a mask for the emoji
# Use a tool like OpenCV's SelectROI to manually define the emoji region.
# Or you can create a binary mask with white (255) for the emoji area and black (0) elsewhere.

# Example: Manually defining a rectangular region (adjust as needed)
mask = np.zeros(image.shape[:2], dtype=np.uint8)
cv2.rectangle(mask, (x_start, y_start), (x_end, y_end), 255, -1)  # Replace (x_start, y_start), (x_end, y_end)

# Use inpainting to fill the emoji area
inpainted_image = cv2.inpaint(image, mask, inpaintRadius=7, flags=cv2.INPAINT_TELEA)

# Save and display the result
cv2.imwrite('output_image.jpg', inpainted_image)
cv2.imshow('Result', inpainted_image)
cv2.waitKey(0)
cv2.destroyAllWindows()
