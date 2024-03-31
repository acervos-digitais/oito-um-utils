## pre-processing

```python
crop_x0 = int(0.58 * width)
crop_x1 = crop_x0 + int(0.4 * width)
crop_y0 = int(0.04 * height)
crop_y1 = crop_y0 + int(0.04 * height)

morph_kernel = cv2.getStructuringElement(cv2.MORPH_RECT, (1, 1))

crop = frame[0:crop_h, crop_x:]
_, thresh = cv2.threshold(cv2.cvtColor(crop, cv2.COLOR_RGB2GRAY), 190, 255, cv2.THRESH_BINARY)
inv_er_di = cv2.dilate(cv2.erode(cv2.bitwise_not(thresh), morph_kernel), morph_kernel)
rgb = cv2.cvtColor(inv_er_di, cv2.COLOR_GRAY2RGB)
```
