scribble notes



Die Puchku (mit weißem Fell in den Bildern) ist erst 7 Monate alt und hatte eine schwere Fraktur aufgrund eines unglücklichen Abstürz erlitten. Ich habe sie zur Tierklinik in München gebracht und dort wurde sie operiert. Die OP hat 1800 Euro gekostet. Ich wäre sehr dankbar, wenn ihr mir mit einer kleinen Spende helfen würdet. So eine lebensfröhe süße kleine Katze konnte ich nicht ihrem Schicksal überlassen und müsste Ich ihr mit der OP einfach helfen. Mittlerweise geht es Puchku gut und kann wieder ihr Bein belasten. Die gesamte Spende geht an das Tierheim Beckenstetten und wird von dort aus zu der Klinik überwiesen. Natürlich kann man die Spende direkt an das Klinikum überweisen. Die gesamte Rechnung und OP Berichte habe ich zur Einsicht hier hochgeladen. Für weitere Fragen, schreib mich bitte gern an. Vielen Dank.


24 dEz 2020 synced




ffmpeg -i Img5562-1.mp4 -af "volume=-15dB" -c:v copy -c:a aac -b:a 192k output.mp4

ffmpeg -i audio_only.m4a -af "volume=-1dB" output.mp3

ffmpeg -i IMG_5562.mp4 -vn -acodec copy audio_only.m4a

ffmpeg -i video.avi -vf subtitles=subtitle.srt out.avi


$ ffmpeg -i a.mkv

ffmpeg -loop 1 -framerate 30 -t 5 -i 28_11_resized.jpg \
       -t 5 -f lavfi -i aevalsrc=0 \
       -i stachus_subtitle.mp4 \
       -filter_complex '[0:0] [1:0] [2:0] [2:1] concat=n=2:v=1:a=1' \
       stachus_subtitle_image.mp4


ffmpeg -loop 1 -framerate 30 -i header.jpg -c:v libx264 -t 3 -pix_fmt yuv420p input.mp4

ffmpeg -i input.mp4 -vf scale=1080x1080,setdar=9:16 output.mp4

ffmpeg -i output.mp4 -c copy -bsf:v h264_mp4toannexb -f mpegts output.ts

ffmpeg -i stachus_subtitle.mp4 -c copy -bsf:v h264_mp4toannexb -f mpegts video.ts

ffmpeg -i "concat:output.ts|video.ts" -c copy -bsf:a aac_adtstoasc stachus_subtitle_image.mp4


Hello World ! I am reaching out to you, because I need your assistance to reach my voice to the responsible authorities, because of massive misuse of Infektionsschutzgesetz.
I want to convey the authorities to stop thinking, that every non-white person is a criminal. 

I was brutally attacked by the police as my wife and myself were eating in the citycenter. The police claimed, that we are not allowed to eat in the city center, because its a mask zone.
We said, we didnt know it and wanted to leave.

The police asked for my ID, and since I didnt have my ID, I wanted to take out my driving license. 
One of the police wrote in his statements, that although he knew, that I wanted to take out my driving license, he didnt let me, because he thought, that I was about to take out a weapon.
When I asked, why are they arresting me, then they didnt give me an answer.

They were 4 policemen and I was alone. They bought me on the floor without any great effort, and to hide their racist mishandling now they are writing in their statement, 
that they arrested me, because I attacked them and threw their body cam on the floor. They claim, that this is also the reason, why they could not start the bodycam.
The most aggressive officer then hit me on the back of my head, as I was already lying on the ground with handcuffs, and thereafter I started bleeding.
They also wrote in the statement, that I tore my jacket myself. 

Would you believe these lies from the police? 

They stripped me and did a body search, and also searched for somethings into my belongings, as if I was a criminal.
Was it required to strip and search me and my belongings, if it was just about the mask? 
My wife and myself are schocked by the entire incident, especially seeing racism and brutality through the police officers.
According to the shops, the police just picks up people randomly from the crowd and misuses the infektionsschutzgestz.

I hope, my voice reaches the passersby who made a video of the incident, so that we can show the government, that the police is lying under oath.




Hallo Welt ! Ich wende mich an Euch, weil ich eure Hilfe brauche, um meine Stimme bei den zuständigen Behörden zu erreichen, weil das Infektionsschutzgesetz durch die Polizei in Deutschland massiv missbraucht wird. Bitte teile diesen Beitrag so oft Du kannst.

Ich wurde von der deutschen Polizei brutal angegriffen, als meine Frau und ich im Stadtzentrum gegessen haben. Die Polizei behauptete, dass wir hier nicht essen dürfen, weil es eine Maskenzone ist.
Wir sagten, dass wir es nicht wussten und daher den Platz verlassen wollten.

Die Polizei fragte mich nach meinem Ausweis und ich wollte meinen Führerschein herausgeben.
Einer der Polizisten schrieb in seinen Aussagen, dass obwohl er wusste, dass ich meinen Führerschein herausgeben wollte, dachte, ich würde gleich eine Waffe herausnehmen und begann mich deshalb zu verhaften.
Als ich fragte, warum sie mich verhaften, gaben sie mir keine Antwort.

Sie waren 4 Polizisten und ich war allein. Sie haben mir ohne große Anstrengung, aber auf sehr brutale Weise, Handschellen angelegt, und um ihren unverhältsmäßigen Missbrauch zu verbergen, lügen sie jetzt in ihrer Aussage.
dass sie mich verhaftet haben, weil ich sie angegriffen und ihre Körperkamera aus ihrer Jacke geworfen habe. Sie behaupten, dass dies auch der Grund ist, warum sie die Bodycam, die in Wirklichkeit eingeschaltet war, nicht starten konnten, bevor sie anfingen, mich zu verhaften. Überraschenderweise sind die Beweise für die Bodycam auf mysteriöse Weise verschwunden.

Der aggressivste Offizier schlug mich dann auf den Hinterkopf, da ich bereits mit Handschellen auf dem Boden lag, und danach begann ich zu bluten.
Sie schrieben auch in der Erklärung, dass ich meine Jacke selbst zerrissen habe, wobei die Wahrheit ist, dass sie mich brutal misshandelt haben.

Sie zogen mich aus und führten eine Körpersuche durch und durchsuchten auch meine Sachen, als wäre ich ein Verbrecher.
War es erforderlich, mich und meine Sachen auszuziehen und zu durchsuchen, wenn es nur um die Maske ging?
Meine Frau und ich sind schockiert über den gesamten Vorfall, insbesondere über Rassismus und Brutalität durch die Polizisten.
Laut den Geschäften in der Gegend gaben sie eine Erklärung ab, dass die Polizei nur zufällig Personen aus der Menge aufnimmt und das Gesetz über Infektionsschutzgesetze missbraucht.

Sind diese Lügen von der Polizei überhaupt zu glauben?

Ich hoffe, meine Stimme erreicht die Passanten, die möglicherweise ein Video des Vorfalls gemacht haben. 

 