media_to_video
==============

Convert your images and videos into videos played consecutively.

Each media file will have a duration of 4 seconds by default & videos
have their audio disabled.

Issues
~~~~~~

-  GetMedia.get\_all(...) will raise an Exception if there's a file
   containing an odd character such as '/'. (e.g.: Exception raised if
   file "my/image.jpg" is encountered)

   -  glob.glob(...) converts '/' to some codes or different type of
      codec

Bugs
~~~~

-  when resizing moviepy Clip object, an error stating tostring()
   function is no longer supported is shown, to **fix**, go to
   .../python2.7/dist-packages/moviepy/video/fx/resize.py and replace
   tostring with tobytes on line 32

-  image files with transparency as a border may be resized to the wrong
   size (problem with pymediainfo possibly)

Requirements
------------

-  Python 3

Modules
^^^^^^^

-  moviepy
-  pymediainfo
-  fire
-  dill
- get-media-files

check requirements.txt

Dependencies
^^^^^^^^^^^^

-  `MediaInfo <https://mediaarea.net/en/MediaInfo/Download>`__ (for
   pymediainfo module)

Install
-------

::

    git clone https://github.com/jtara1/media_to_video.git

    cd media_to_video


media_to_video.__main__
-----------------------

Description: Takes media files from a folder, concatenates them, and
writes them to a file using GetMedia class and moviepy module.

Input: list of files (path)

Output: renders and saves the output video in a folder called `output` relative to where the input path is


Usage
-----

Check cli options with `python3 media_to_video` which runs the __main__.py
The cli uses fire module so you need to call the method render to render after
the arguments for MediaToVideo are given.

::
    python3 media_to_video --src-path /home/user/media_files render

    python3 media_to_video --src-path /home/user/media_files render --continuous True

    python3 media_to_video --src-path /home/user/media_files --dont_load_renders_heap True render --continuous True