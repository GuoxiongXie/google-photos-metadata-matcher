## Migrate Google Photos

1. Export photos in https://takeout.google.com/
2. Extract files into one folder
  
      If you have multiple .zip files you can extract with `ditto` in `macos`
        
        ditto -x -k *.zip ./takeout_photos
       
3. install dependencies of this project

       cd google-metadata-matcher
       pip3 install -r requirements.txt

4. Run the metadata merger on the images

       python3 src/merge_metadata.py <source_directory> <output_directory>


## Google photos takeout metadata merging into their images

Original windows based version: [GooglePhotosMatcher](https://github.com/anderbggo/GooglePhotosMatcher)

This is a command line version which based on Python3 runtimer only (Mac / Windows / Linux)

Takes a folder, collects all `.json` files which contain the metadata of the image, convert the image to `.jpg` and apply the metadata to it.

```
usage: merge_metadata.py [-h] [-w EDITED_WORD] [-o OPTIMIZE] [-m MAX_DIMENSION] source_folder output_folder

positional arguments:
  source_folder
  output_folder

optional arguments:
  -h, --help            show this help message and exit
  -w EDITED_WORD, --edited_word EDITED_WORD
                        Google Photos 'edited' word translation
  -o OPTIMIZE, --optimize OPTIMIZE
                        Optimalize the images (0 to 100), recommended: 75 (default: disabled)
  -m MAX_DIMENSION, --max_dimension MAX_DIMENSION
                        Resize the image restricting the max width,height dimension
```

## Features

- Keeps Geo cordinates
- Keeps creation time
- Recursive folders image merging
- PNG, HEIC Support
- Resize option
- Optimalization option

## Main Dependencies

- Pillow - Image Editor lib
- pillow-heif - Image Editor lib HEIC (Apple) support
- piexif - Adjust Metadata for image