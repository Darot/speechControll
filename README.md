# Speech Control

On work in Debian-based systems:

# Python Requirements

``` 
pip install python
pip install SpeechRecognition
```

# Quick start on SpeechRecogniton python module.

The Linux audio stack is pretty fickle. There are a few things that can cause these issues.
First, make sure JACK is installed - to install it, run sudo apt-get install multimedia-jack

You will then want to configure the JACK daemon correctly to avoid that “Cannot allocate memory” error. Run sudo dpkg-reconfigure -p high jackd2 and select “Yes” to do so.

Now, you will want to make sure your current user is in the audio group. You can add your current user to this group by running sudo adduser $(whoami) audio.

Unfortunately, these changes will require you to reboot before they take effect.

After rebooting, run pulseaudio --kill, followed by jack_control start, to fix the “jack server is not running or cannot be started” error.


## Commom usage

```python
import speech_recognition as sr

r = sr.Recognizer()
with sr.Microphone() as source:                # use the default microphone as the audio source
    audio = r.listen(source)                   # listen for the first phrase and extract it into audio data

try:
    print("You said " + r.recognize(audio))    # recognize speech using Google Speech Recognition
except LookupError:                            # speech is unintelligible
    print("Could not understand audio")
```


#### References

https://pypi.python.org/pypi/SpeechRecognition/

http://stackoverflow.com/questions/12239080/getting-started-with-speech-recognition-and-python

#### Futher reading

```
http://www.nltk.org/
```


# Install
Short description(follow these commands):

    Install build dependencies (on ubuntu):

    sudo apt-get build-dep python-pygame

    Install mercurial to use hg (on linux):

    sudo apt-get install mercurial

    Use pip to install PyGame:

    pip install hg+http://bitbucket.org/pygame/pygame

    If the above gives freetype-config: not found error (on Linux), then try sudo apt-get install libfreetype6-dev and then repeat 3.


## Debian-based 
```
sudo apt-get install python python3
sudo apt-get install python-pip python3-pip
sudo apt-get install flac
sudo pip install pyttsx
sudo apt-get install multimedia-jack
sudo dpkg-reconfigure -p high jackd2 and select “Yes”
sudo adduser $(whoami) audio
pulseaudio --kill
jack_control start
```
