###Tesseract 4 for macOS


I am writing on how to install tesseract on macOS. The version of macOs I am using is 10.14.3 Mojave but this code should work for any other versions too. Please make sure you have homebrew installed before you begin, also make sure that you remove previous versions of tesseract. In my case I had installed tesseract 3 using macports so I had to uninstall it first using

```sudo port uninstall tesseract.```

To begin installation of Tesseract4 open Terminal and type:

```
brew install automake autoconf libtool
brew install pkgconfig
brew install icu4c
brew install leptonica
brew install gcc
brew install pango

git clone https://github.com/tesseract-ocr/tesseract/
cd tesseract
./autogen.sh
./configure CC=gcc-8 CXX=g++-8 CPPFLAGS=-I/usr/local/opt/icu4c/include LDFLAGS=-L/usr/local/opt/icu4c/lib
make -j
sudo make install  # if desired
make training # if installed with training dependencies

```



This is the error I am getting after I installed above dependencies 

```
ajinkyas-MacBook-Pro:Downloads ajinkyabobade$ tesseract text.jpg -l eng

Error opening data file /usr/local/share/tessdata/eng.traineddata
Please make sure the TESSDATA_PREFIX environment variable is set to your "tessdata" directory.
Failed loading language 'eng'
Tesseract couldn't load any languages!
Could not initialize tesseract.
```

To resolve it and run tesseract normally do the dollowing:

```
cd  /usr/local/share/tessdata/
configs		pdf.ttf		tessconfigs

sudo wget  https://github.com/tesseract-ocr/tessdata_best/raw/master/eng.traineddata
```


Now run : tesseract -v 
After this to test your image run : tesseract text.jpg output
This will generate extracted OCR into another text file named output.txt 
 

 
