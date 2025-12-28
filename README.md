## Day X – HSV color masks & multi-color contours

In this session I moved from grayscale contour detection to **color-based segmentation** using the HSV color space.

### What I implemented

- Converted the input image from BGR to HSV using `cv2.cvtColor`.
- Built separate HSV ranges for **red, blue and green** objects.
- Created binary masks with `cv2.inRange(hsv, lower_color, upper_color)`.
- Extracted color-only images using `cv2.bitwise_and`.
- Found contours **on the color masks** (`cv2.findContours`) and drew them on the original image.

The final pipeline looks like this:

# HSV-mask
creating contours through making HSV mask instead of grayscale

This was my first *multi-color* pipeline:  
one function receives an image, builds three masks (red, blue, green),  
creates `red_only`, `blue_only`, `green_only`, and finally returns an image with all contours drawn.

### Key lessons

- HSV makes it much easier to isolate colors by tuning **H, S, V** thresholds.
- Red often needs **two H ranges** (around 0 and around 180) while blue and green work well with a single range.
- Contours become more stable when they are computed on **clean color masks** instead of noisy grayscale images.
