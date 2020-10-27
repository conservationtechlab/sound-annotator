# sound-annotator

GUI tool for annotating sound events manually from a spectrogram and
audio playback.  Built by Gabriel Cano during a summer fellowship with
the San Diego Zoo Conservation Technology Lab.

The application is meant to use WAV files as input and works best for
those created by AudioMoth devices.

The application has been tested the most on macOS (Mojave and
Catalina) but has also been used on Ubuntu 18.04.

## Setup
Clone the repo. For help check these
[instructions](https://help.github.com/en/github/creating-cloning-and-archiving-repositories/cloning-a-repository).

Create a virtual environment and activate it. For help check these
[instructions](https://docs.python.org/3/tutorial/venv.html).

Install pip if needed. For help check these
[instructions](https://pip.pypa.io/en/stable/installing/).

Download dependencies by running:
`pip install -r requirements.txt`

On Ubuntu: you may have to install some additional Debian packages
(e.g. sudo apt install libasound2-dev).  These include (but may not be
limited to):

- libasound2-dev

To run program:
`python3 main.py`

![Alt text](/screenshots/start.png?raw=true "Starting Screen")

## Start a new session
File -> New Session

This opens a dialog box where you can type or choose the:

- data path (the path of the folder where the WAV files are stored)

- save path (file for csv annotation record (path is optional but
filename is not optional (at time of this writing filename absence
results in crash). File does not need to already exist.)

The "Minimum Duration" value you supply will force selections to be at
least that many seconds long.

![Alt text](/screenshots/new_session.png?raw=true)

## Load a previous session
File -> Load Session

This opens a file browser where you need to select the configuration
file (.yaml) saved when ending a previous session. It will open the
session to the WAV file you left off on and it will continue saving to
the same csv output file.

## Create an annotation

Drag the mouse over a part of the spectrogram. Press the play button
or Action -> Play to listen to the selection. Press the save button or
Action -> Save to save an annotation with the specified tag in the
textfield above the buttons.

![Alt text](/screenshots/create_anno.png?raw=true)

The annotation has a filepath (fp) which is the full filepath to where
the audio file resides. Next is the tag which is specified by the user
in the textfield. The next two entries are the start and end index of
the selection in the original audio data. Finally the sampling rate
(sr) is specified in case the data is loaded as a spectrogram with a
different sampling rate than the original audio file.

## Edit an annotation

Find the information you would like to edit in the table. Click on an
entry to edit it. The original csv file is changed to match when you
click elsewhere. Currently there is no way to delete a row but you can
erase the entry.

![Alt text](/screenshots/edit_tag.png?raw=true)

## Move to a different file

Use the previous and next button or Action -> Previous and Action ->
Next.

## Save a session

Saving a session is for convenience. It does not affect whether the
csv file is saved or not because the annotations are always saved the
moment they are created.

Python -> Quit Python

This brings up a dialog box where you are given the option to save the
current session. If you choose yes you provide a filename and choose
where to save it.

![Alt text](/screenshots/save_session.png?raw=true)

Warning: If you press the "x" button the application will close
without saving your session (however your annotations are saved the
moment you create them).

## Browse audio files visually

Create a session normally and use a dummy save file.

## Forgot to save session but want to continue annotating 

Simply start a new session again and instead of creating a new save
file select the one you were using before (for some reason the dialog
box will disappear behind the application, just move the application
out of the way and press ok on the box). By default, the spectrogram
shown will be the first. You can use Actions -> Goto to skip ahead.




