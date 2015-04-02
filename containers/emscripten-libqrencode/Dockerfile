FROM emscripten-ubuntu

MAINTAINER samhrussell

RUN apt-get update

RUN apt-get install -y autoconf libtool libsdl-dev

WORKDIR libqrencode

RUN git clone -b 3.4 git://github.com/samrussell/libqrencode

WORKDIR libqrencode

RUN mkdir m4

RUN echo "./autogen.sh" > buildlibqrencode.sh
# sed -i "s/as_fn_error \$? \"Package requirements .\+libpng.\+/\$as_echo \"libpng fail/g" configure
RUN echo "sed -i \"s/as_fn_error \\\$? \\\"Package requirements .\+libpng.\+/\\\$as_echo \\\"libpng fail/g\" configure" >> buildlibqrencode.sh
RUN echo "/emsdk_portable/emscripten/master/emconfigure ./configure --enable-static --prefix=/volume" >> buildlibqrencode.sh
RUN echo "sed -i '/^DEFAULT_INCLUDES/ s/$/ -I\/volume\/include/' Makefile" >> buildlibqrencode.sh
RUN echo "/emsdk_portable/emscripten/master/emmake make" >> buildlibqrencode.sh
RUN echo "/emsdk_portable/emscripten/master/emmake make install" >> buildlibqrencode.sh
RUN echo "/emsdk_portable/emscripten/master/emcc qrencode-qrenc.o /volume/lib/*.a -o /volume/bin/qrencode.html" >> buildlibqrencode.sh

RUN chmod 755 buildlibqrencode.sh

CMD ./buildlibqrencode.sh
