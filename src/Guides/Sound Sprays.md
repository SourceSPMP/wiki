{{Author|bandit}}
# Sound Sprays

1. Convert your sound to a 22050 hz mono WAV file. (You can use ffmpeg or audacity for this)
2. Place it in the sound folder
3. In the game, do `cl_customsounds 1`
4. Then do `cl_soundfile sound/YOUR SOUND FILE NAME.wav`
5. To play the sound, do `impulse 202` (you can bind it to a key)

For context, a sound spray is a sound file that you can play in game, like a TF2 noise maker.
It uses the same cooldown as a spray (decalfrequency) and can be customised, hence the name "Sound Spray".