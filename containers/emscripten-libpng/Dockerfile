FROM emscripten-ubuntu

MAINTAINER samhrussell

WORKDIR libpng

RUN wget http://download.sourceforge.net/libpng/libpng-1.6.16.tar.gz

RUN tar -xzf libpng-1.6.16.tar.gz

WORKDIR libpng-1.6.16

# sed -i '/zlib not installed/c\$as_echo "ignoring zlib check"' configure
# sed -i '/^DEFAULT_INCLUDES/ s/$/ -I\/volume\/include/' Makefile

RUN echo "sed -i '/zlib not installed/c\$as_echo \"ignoring zlib check\"' configure" > buildlibpng.sh
RUN echo "/emsdk_portable/emscripten/master/emconfigure ./configure --enable-static --prefix=/volume" >> buildlibpng.sh
RUN echo "sed -i '/^DEFAULT_INCLUDES/ s/$/ -I\/volume\/include/' Makefile" >> buildlibpng.sh
RUN echo "/emsdk_portable/emscripten/master/emmake make" >> buildlibpng.sh
RUN echo "/emsdk_portable/emscripten/master/emmake make install" >> buildlibpng.sh

RUN chmod 755 buildlibpng.sh

RUN ls

CMD ./buildlibpng.sh
