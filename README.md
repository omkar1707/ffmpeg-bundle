ffmpeg-bundle
===========

[FFmpeg](http://ffmpeg.org/) module for [Node](http://nodejs.org/).
This library provides a set of functions and utilities to abstract commands-line usage of ffmpeg. This library comes with platform independent ffmpeg binaries.

You can install this module using [npm](http://github.com/isaacs/npm):

	npm install ffmpeg-bundle

## Usage

To start using this library, you must include it in your project and then you can either use the callback function or through the [promise](https://github.com/cujojs/when) library:

	var ffmpeg = require('ffmpeg-bundle');

```
async function process(inputFile, outputFile) {
    return new Promise(function (resolve, reject) {
        try {
            let process = ffmpeg(inputFile);
            process.then(function (video) {
                video.save(outputFile, function (error, file) {
                    if (!error) {
                        console.log('Video file: ' + file);
                        resolve(file);
                    } else {
                        console.log(error);
                        reject(error);
                    }
                });

            }, function (err) {
                console.log('Error: ' + err);
                reject(err);
            });
        } catch (e) {
            console.log(e.code);
            console.log(e.msg);
        }
    });
}
```

## Reference
This library is combination of below two libraries

[node-ffmpeg](https://github.com/damianociarla/node-ffmpeg)

[@ffmpeg-installer/ffmpeg](https://github.com/kribblo/node-ffmpeg-installer)
