Uploadr.py
==========

Uploadr.py is a simple Python script for uploading your photos to Flickr. Unlike
many GUI applications out there, it lends itself to automation; and because it's
free and open source, you can just change it if you don't like it.


Authentication
--------------

To use this application, you need to obtain your own Flickr API key and secret
key. You can apply for keys `on the Flickr website
<http://www.flickr.com/services/api/keys/apply/>`_.

When you have got those keys, you need to set environment variables so that they
can be used by this application. For example, if you use Bash, add the following
lines to your ``$HOME/.bash_profile``::

    export FLICKR_UPLOADR_PY_API_KEY=0123456789abcdef0123456789abcdef
    export FLICKR_UPLOADR_PY_SECRET=0123456789abcdef


Use with Mac Folder Actions
---------------------------

This version has been customized to work with an Apple Script that detects when
images have been added into the folder. To setup:

* Go to /Library/Scripts/Folder Action Scripts/
* Add a new script with the content below. You will need to adjust the paths to match what is one your machine::

    property dialog_timeout : 30 -- set the amount of time before dialogs auto-answer.

    on adding folder items to this_folder after receiving added_items
        try
            do shell script "/usr/local/bin/python2.7 ~/uploadr.py/uploadr/uploadr.py >> ~/uploadr.py/uploadr/uploader.log"
        end try
    end adding folder items to


* Right click on the images folder, go to Services > Folder Action Setup
* Add your new script. Make sure it is checked
* Also make sure the 'Enable Folder Actions' box is checked in the upper left
* You should run the script manually the first time to authenticate and make sure it works::

    $ python uploadr.py -d


License
-------

Uploadr.py consists of code by Cameron Mallory, Martin Kleppmann, Aaron Swartz and
others. See ``COPYRIGHT`` for details.
