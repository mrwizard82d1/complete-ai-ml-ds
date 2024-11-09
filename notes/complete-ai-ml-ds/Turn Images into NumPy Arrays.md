Copy three examples into `images/`

Render one of the images in a markdown cell
- `img src='images/panda.png' />`

Use `matplotlib` to read an image from a file into an array
- Although the video uses `matplotlib.imread`, the documentation for this function recommends using `PIL.image.open` which I can do also. That is the approach I will use.

Read `images/panda.png`
- Import `from PIL import Image`
- `panda = np.array(Image.open('images/panga.png'))`
- `type(panda)`
- `panda.size, panda.shape, panda.ndim`

Read `images/car-photo.png`
- `car = np.array(Image.open('images/car-photo.png'))`
- `type(car)` 

Read `images/dog-photo.png`
- `dog = np.array(Image.open('images/dog-photo.png'))`
- `type(dog)` 

People can recognize an image; `numpy` only recognizes numbers.
- Needed to process images
