# Libnyquist


Platform | Build Status |
-------- | ------------ |
Microsoft VS2017 x64 | [![Build status](https://ci.appveyor.com/api/projects/status/2xeuyuxy618ndf4r?svg=true)](https://ci.appveyor.com/project/ddiakopoulos/libnyquist) |
Clang (OSX) & GCC (Linux) | [![Build Status](https://travis-ci.org/ddiakopoulos/libnyquist.svg?branch=master)](https://travis-ci.org/ddiakopoulos/libnyquist) |

Libnyquist is a small C++11 library for reading sampled audio data from disk or memory. It is intended to be used an audio loading frontend for games, audio sequencers, music players, and more.

The library does not include patent or license encumbered formats (such as AAC). For portability, libnyquist does not link against platform-specific APIs like Windows Media Foundation or CoreAudio, and instead bundles the source code of reference decoders as an implementation detail.

Libnyquist is meant to be statically linked, which is not the case with other popular libraries like libsndfile (which is licensed under the LGPL). Furthermore, the library is not concerned with supporting very rare encodings (for instance, A-law PCM or the SND format). 
 
While untested, there are no technical conditions that preclude compilation on other platforms with C++11 support (Android NDK r10e+, Linux, iOS, etc).
+ ALSA
    [WIKI](https://wiki.archlinux.org/title/Advanced_Linux_Sound_Architecture_(%E7%AE%80%E4%BD%93%E4%B8%AD%E6%96%87)#.E4.BB.8D.E7.84.B6.E6.B2.A1.E6.9C.89.E5.A3.B0.E9.9F.B3.EF.BC.9F%E2%80%94%E2%80%94%E2%80%94%E2%80%94%E2%80%94%E2%80%94%E2%80%94%E2%80%94%E2%80%94%E2%80%94%E2%80%94%E2%80%94%E2%80%94%E2%80%94%E2%80%94%E2%80%94%E7%89%88%E6%9D%83%E5%A3%B0%E6%98%8E%EF%BC%9A%E6%9C%AC%E6%96%87%E4%B8%BACSDN%E5%8D%9A%E4%B8%BB%E3%80%8C%E5%B1%9E%E7%89%9B%E3%80%8D%E7%9A%84%E5%8E%9F%E5%88%9B%E6%96%87%E7%AB%A0%EF%BC%8C%E9%81%B5%E5%BE%AACC%204.0%20BY-SA%E7%89%88%E6%9D%83%E5%8D%8F%E8%AE%AE%EF%BC%8C%E8%BD%AC%E8%BD%BD%E8%AF%B7%E9%99%84%E4%B8%8A%E5%8E%9F%E6%96%87%E5%87%BA%E5%A4%84%E9%93%BE%E6%8E%A5%E5%8F%8A%E6%9C%AC%E5%A3%B0%E6%98%8E%E3%80%82%E5%8E%9F%E6%96%87%E9%93%BE%E6%8E%A5%EF%BC%9Ahttps://blog.csdn.net/xwinie/article/details/88346286)
    ```shell
    # for The Advanced Linux Sound Architecture API.
    sudo apt-get install libalsa-ocaml-dev
  
    # use LINUX_ALSA
    cmake -D LIBNYQUIST_ASOUND=1 ../
    ```
  + OSX
  ```shell
  cmake -DAPPLE=1 ../
  ```


## Format Support

Regardless of input bit depth, the library produces a channel-interleaved float vector, normalized between [-1.0,+1.0]. At present, the library does not provide comprehensive resampling functionality. 

* Wave (+ IMA-ADPCM encoding)
* MP3
* Ogg Vorbis
* Ogg Opus
* FLAC
* WavPack
* Musepack

## Known Issues & Bugs
* See the Github issue tracker. 

## License
This library is released under the simplied 2 clause BSD license. All included dependencies have been released under identical or similarly permissive licenses.
