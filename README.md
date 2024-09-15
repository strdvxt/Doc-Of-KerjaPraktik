"# Doc-Of-KerjaPraktik" 
"# Doc-Of-KerjaPraktik" 

             
Dokumentasi Kerja Praktik 
Nama : Nyimas Anggun Barokatillah
Mentor : Pak Jusan (Sistem)
19 Juni 2024
Apa itu VOIP?
VOIP stands for Voice Over Internet Protocols. Maksudnya apa? Voip memungkinkan pengiriman suara dalam bentuk data melalui jaringan internet atau jaringan IP. Teknologi ini memungkinkan pengguna untuk melakukan panggilan telepon melalui internet, dengan mengubah suara analog menjadi digital dan mengirimkannya melalui jaringan IP. VoIP memungkinkan pengguna untuk berkomunikasi dengan biaya yang lebih rendah daripada menggunakan sistem telepon tradisional. (Sailellah, 2023)
Singkatnya VOIP bisa mengirimkan paket suara melalui internet, contoh yang tidak asing adalah WhatsApp Phone Calls. 
Apakah ada jenis VOIP yang bisa diintegrasi dari internet? IP Phones IP Phone merupakan telepon khusus yang telah dirancang untuk terhubung ke jaringan internet melalui Ethernet atau Wi-Fi. Biasanya, IP Phone digunakan oleh perusahaan atau bisnis kecil dan menengah. Sepertinya jenis ini bisa di telusuri lebih dalam.
Sekarang, apakah bisa VOIP menggunakan mikrokontroller?
ESP32 ADF(Audio Development Framework)
Dokumentasi ESP32 ADF https://github.com/espressif/esp-adf?tab=readme-ov-file
Install ESP IDF yang sesuai , berdasarkan : 
Link instal : https://dl.espressif.com/dl/esp-idf/?idf=4.4 (pada kasus ini aku pilih ESP IDF v 4.4.7 offline installer) sebelumnya mencoba yang online installer, lebih sulit.
Okay, jangan lupa download Espressif IDE nya juga di link install yg sama
Saat mencoba mengkoneksikan board dengan example di terminal eror terus. Berikut ini masalahnya 
A fatal error occurred: Failed to connect to ESP32: Invalid head of packet (0x08): Possible serial noise or corruption.
For troubleshooting steps visit: https://docs.espressif.com/projects/esptool/en/latest/troubleshooting.html
CMake Error at run_serial_tool.cmake:56 (message):
  C:/Espressif/python_env/idf4.4_py3.11_env/Scripts/python.exe
  C:/Espressif/frameworks/esp-idf-v4.4.7/components/esptool_py/esptool/esptool.py
  --chip esp32 failed
FAILED: CMakeFiles/flash C:/Espressif/frameworks/esp-idf-v4.4.7/examples/get-started/hello_world/build/CMakeFiles/flash
cmd.exe /C "cd /D C:\Espressif\frameworks\esp-idf-v4.4.7\components\esptool_py && C:\Espressif\tools\cmake\3.23.1\bin\cmake.exe -D IDF_PATH="C:/Espressif/frameworks/esp-idf-v4.4.7" -D SERIAL_TOOL="C:/Espressif/python_env/idf4.4_py3.11_env/Scripts/python.exe C:/Espressif/frameworks/esp-idf-v4.4.7/components/esptool_py/esptool/esptool.py --chip esp32" -D SERIAL_TOOL_ARGS="--before=default_reset --after=hard_reset write_flash @flash_args" -D WORKING_DIRECTORY="C:/Espressif/frameworks/esp-idf-v4.4.7/examples/get-started/hello_world/build" -P C:/Espressif/frameworks/esp-idf-v4.4.7/components/esptool_py/run_serial_tool.cmake"
ninja: build stopped: subcommand failed.
ninja failed with exit code 1
Problem solved : saat connecting press boot and RST at the same time for 3 sec then release RST
Masalah lain : serial monitor gak baca  
Problem solved : ga di apa apain Cuma cabut colok bisa jalan. First hello world!
 

Cara bikin project diterminal:
cd %userprofile%\esp\hello_world
idf.py set-target esp32
idf.py menuconfig

20 juni 2024
Btw, kenapa ESPRESSIF IDE dan ESP-IDF?
Bahasa yg digunakan adalah C/C++ dan python tooling, banyak komponen, terintegrasi dengan network,dan ada komponen manager, konfigurasi level komponen dan support Kconfig, aktif di aintain, cepet buat dapet fitur baru, kemudahakn penggunaan dengan commandline support dan optional IDE support, GDB support dan banyak fitur debbunging
 Cara pakenya gimana?
Pake environment eclipse on windows
Install system packages=>ESP-IDF=> toolchain dan python virtual environment
Project Workflow
1.	Configure, set konfigurasi dari tiap komponen dan generate sdkconfig file
2.	Build, compile sumber file dari semua komponen. Link dan generate project binary
3.	Flash, reset ESp32 ke friemware download mode. Tulis binary ke flash memory
4.	Monitor, reset esp32 ke eksekusi mode. Monitor log keluaran menggunakan idf.py monitor

Flash?
In command line :
     
Looks like so needy to do flash

How to programm??
I don’t have any idea honestly. Lol. They talk about FreeRTOS. Scheduling algoritm??
Memory model?
Component adalah library yang lebih banyak hal…
https://docs.espressif.com/projects/esp-adf/en/v2.0/get-started/index.html
kalua dari sini instal esp nya pake toochain dulu (MINGW32) idk what its mean but shall we try it?
Bagus sih tapi agak ribet ya jadi balik lagi ke cara awal
Hmm
https://github.com/espressif/esp-adf/releases harusnya cloning yg ini, ambil versi yg spesifik dan lakukan sesuai yg ada di sana
sama aja ..

21 Juni 2024
File exe espressif tidak dapat dibuka karena masalah ‘path’
Using Embedded Python 3.11.2
Using Embedded Git :
      C:\Espressif\tools\idf-git\2.44.0\cmd\git.exe
Will install ESP-IDF 5.2.2 into:
      C:\Espressif\frameworks\esp-idf-v5.2.2
IDF tools directory (IDF_TOOLS_PATH): 
      C:\Espressif
Components: Eclipse 
Drivers: FTDI Sillicon Labs Espressif WCH 
Targets: ESP32 ESP32-C3 ESP32-S2 ESP32-S3 

1.	Install versi IDF yang sudah stabil
2.	Install di :C
3.	Full installation udh itu kalua udh selesai powershell sm cmd nya lgsg tutup aja trs buka espressif iDE yang udh ada shortcut nya
4.	Terus langsung proses tools tools nya
Saat sudah masuk ke menu awal dan mau nyoba codingan examples:
1.	Pilih mau yg mana codingannya blink/hello world
2.	Clean prodect sebelum mulai
3.	Build project
4.	Set target, pake esp32
5.	Pilih port
6.	Lalu build dengan tanda palu di pojok kiri
7.	Lalu Run
Pertama kali koding Bahasa C di espressif pake library freeRTOS
#include <stdio.h>
#include "freertos/FreeRTOS.h"
#include "freertos/task.h"
#include "portmacro.h"

void vTask1fuction(void* pvParamaters){
	for(;;){
		printf("Tis is Task 1\n");
		vTaskDelay(1000/portTICK_PERIOD_MS);
	}
}

void app_main(void){
	xTaskCreate(vTask1fuction, "TASK1",1024*2, NULL,5, NULL);
}

An overview : https://docs.espressif.com/projects/esp-idf/en/stable/esp32/api-reference/system/freertos_idf.html 
But, what is RTOS?
Setiap core pada prosesor di suatu komputer hanya dapat mengerjakan satu tugas komputasi dalam satu waktu. bagaimana dengan mikrokontroler yang kebanyakan hanya memiliki satu core pada prosesornya? Apakah ada cara untuk membuat tugas-tugas komputasi di mikrokontroler dikerjakan secara bersamaan?
 
Baca : https://medium.com/dagozilla-itb/pengenalan-real-time-operating-system-rtos-99908e80805a 
ada yang namanya ‘scheduler’. Scheduler memecah tugas-tugas komputasi menjadi beberapa bagian, menjadwalkan eksekusi dari bagian-bagian itu berdasarkan suatu skala prioritas, lalu dieksekusi dengan peralihan antar bagian yang terjadi dengan sangat cepat sehingga tercipta ilusi multitasking.
Ide sederhana dari RTOS adalah untuk mengerjakan tugas-tugas tersebut secara independen dan bergantian dengan penjadwalan yang teratur. RTOS akan membantu kita untuk menyelesaikan masalah penjadwalan eksekusi tugas dengan memanfaatkan kemampuan prosesor dengan seefisien mungkin. 
This is my first simple multiple task using FreeRTOS using espressif IDE
 

Selanjutnya mencoba membuat komponen 
 

Kalua ada masalah cmake ga bis abaca new component, bisa gini
 
Katanya, esp32 punya dual-core … 
Yuk coba kita pake 2 2 nya!
 

Sekarang saatnya.. konfigurasi ADF yayy
 
 
Here we go again .. kemungkinan salah pathnya. 
 
Gotcha!
Lanjut coba file examples>get-started>play_mp3_control
 
Masalah yg sama kayak kemarin kalu diliat dr terminal
Opsi selanjutnya.. coba download adf versi 2.5 (sebelumnya yg udh dicoba v2.6)
 
Eror yg sama..
Mungkinnn masalah pathhh. Yep
24 Juni 2024
Referensi : https://youtu.be/ajR2bJJ-Erw?t=251 
Di video dia hanya buka reference dan edit path idf di environmentnya lalu klik ok dan bug nya hilang. Di kasus yg saya coba, bug nya tidak hilang
 
Mungkin awalnya dari sini Cuma cukup asing sama masalah nya udh dicari juga penempatan git nya ga malasalah. Di path juga ga ada spasi jadi blm tau kenapa.

 
Ini git found yah. 
The eror : 
 
Solved genti file example ke yg ver 2.6 adf
Masalah lain :
 
Coba cara lain… pakai Visual Studio Code
https://www.youtube.com/watch?v=VTQuxmYqLss&list=PLYLmlWn2TdRz0JpgzJuFdBxxCkQwvTwUG&index=3 itss much much more easier. Lol.
-	Set com
-	Set target
-	Sdk config (optional)
-	Build project
-	Flash
-	Rst
Another first hello world
 

In Visual Studio Code, select menu "View" and "Command Palette" and type [configure esp-idf extension]. After, choose the ESP-IDF: Configure ESP-IDF Extension option. You can also choose where to save settings in the setup wizard.
25 Juni 2024
Supported Features
•	Setup, will help you to quickly install ESP-IDF and its relevant toolchain with just few clicks.
•	Build, with one click build and multi target build, you can easily build and deploy your applications.
•	Flash, with both UART and JTAG flash out of the box.
•	Monitoring comes with built-in terminal where you can trigger IDF Monitor Commands from within VS Code as you are used to in traditional terminals.
•	Debugging <https://github.com/espressif/vscode-esp-idf-extension/blob/master/docs/tutorial/debugging.md>, with out of box hardware debugging and also support for postmortem debugging like core-dump, you can analyze the bugs with convenience.
•	GUI Menu Config, provides with simplified UI for configuring your chip.
•	App & Heap Tracing, provides support for collecting traces from your application and simplified UI for analyzing them.
•	System View Tracing Viewer, aims to read and display the .svdat files into trace UI, we also support multiple core tracing views.
•	IDF Size Analysis Overview presents an UI for binary size analysis.
•	`Rainmaker Cloud <https://rainmaker.espressif.com/>`_, we have inbuilt Rainmaker Cloud support where you can edit/read state of your connected IoT devices easily.
•	Code Coverage, we have inbuilt code coverage support which shall highlight in color which line have been covered. We also render the existing HTML report directly inside the IDE.
Src : https://docs.espressif.com/projects/esp-idf/en/v4.2.3/esp32/get-started/vscode-setup.html 

Akhirnya dicoba di computer pak jusan bisa..
Udh bisa plays_mp3_control
Udh itu mau coba protocol voipnya. Tapi masih kendala belum paham basicnya. Apa itu SIP? URI? UDP? 
26 Juni 2024
Espressif's self-developed SIP (Session Initialization Protocol)
Initiate, control, end
  
 
SIP is only involved in the signaling operations of a media communication session and is primarily used to set up and terminate voice or video calls. SIP can be used to establish two-party (unicast) or multiparty (multicast) sessions. It also allows modification of existing calls. The modification can involve changing addresses or ports, inviting more participants, and adding or deleting media streams. SIP has also found applications in messaging applications, such as instant messaging, and event subscription and notification.
Every resource of a SIP network, such as user agents, call routers, and voicemail boxes, are identified by a Uniform Resource Identifier (URI)

I found something
 
lyraT not compatible ro use protocols voip exemple, BBRRUH
https://github.com/espressif/esp-adf/blob/release/v2.4/examples/README.md 
tapii adf v2.4 bisaaaaa
hmm
https://www.esp32.com/viewtopic.php?t=6810 … looks so hard tho
harus install sip pbx

27 Juni 2024
Hari ini install adf 2.4 di computer pak jusan
Instalasi asterisk platform tidak bisa menggunakan windows harus linux…
Jadi ganti ke kamailio harusnya bisa di windows sih, required nya openssl dan mariadb
Saat menginstall mariadb kendalanya adalah setup wizardnya ga ada stelah di extract. Genti pake format msi bisa
Tapi direkomendasikan pakai feeswitch
Sekarang lagi belajar menggunakan freeswitch
 
Belum bisa dicob akarena verifikasinya bermasalah hars telfon sedangkan telfonnya kadang ada suara kadang tidak
Dan
Bhs china 
Tapi boleh untuk dicoba
 
28 Juni 2024
Dengan menginstall aplikasi Zoiper pada android itu bisa dapet BTS seluler?! (jujur ga tau ya masa bikin tower)
Ada central telepon ada pesawat telepon. Kalua di computer pesawatnya bisa make software kayak ikiga, yate, dll. Kl di android Zoiper ikiga?? 
Central juga banyak ada asterisk freepbx switch, kamailio, share openshare, yate dll.
Yate punya alat yg bisa lgsg 5G. 
OpenSIPS ga beginner friendly, cukup ribet. Kalua mau enak dikit bisa pake kamailio, instalasinya lbh mudah. Tapi yg lebih mudah adalah asterisk.
*tanya google*
 

Katanya bisa?? Hmm
https://www.youtube.com/watch?v=A8AQZw5qulo&t=1827s nice pa onno
fyi : IP addres ada yg static dan dynamic

1.	Buat voip sever sendiri, pakai mizu
Referensi : https://www.youtube.com/watch?v=RkhlQUHuwU0 
 
 
Not bad.
 di windows 
Device 1 nya di android pakai Zoiper
 
OMG IT WORKS
Server : MiZu VOIP (windows)
User 1 : 3CX (windows)	
User 2 : Zoiper (android)
Harus terkoneksi di wifi yang sama

8 Juli 2024 (back to work after KRI)
Set up config and wizard on mizu
 
JANGAN LUPA SEMUA DEVICE HARUS NYAMBUNG DI WIFI YG SAMA
Bedanya VoIP, PABX (private automatic branch exchange) dan IVR???
VoIP : komunikasi multimedia melalui internet
PABX : centralnya
IVR : aplikasi dalam PABX

#1 ATTEMPT
ADF master
IDF 5.1.2
Example>protocols>voip
Wifi cant connect???????
Bisa tapi
    ) 
Coba ganti ke idf 4.4.7
(makin parah ga bisa)
Ganti lagi tapi terminalnya ga kebaca apa apa. Kadang terminal kebaca kadang ngga 
Ga ada tulisan apa apa aja
Ini malahnya drivernya nabrak. Jadi ada driver i2s baru yang ga bisa kerja sama driver warisan i2s (legacy i2s driver)
Github masalah serupa : https://github.com/espressif/esp-adf/issues/991 
Harusnya seprti ini 
https://github.com/espressif/esp-adf/tree/master/examples/protocols/voip 

kayaknya ga bisa https://github.com/espressif/esp-adf/blob/master/examples/README.md#compatibility-of-examples-with-espressif-audio-boards 
9 Juli 2024
Apa itu I2S?
Inter IC Sound protocol : dibuat untuk menyambungkan standard di perangkat audio digital.
https://www.allaboutcircuits.com/technical-articles/introduction-to-the-i2s-interface/ 
ADC. Resolusi tergantung jumlah bits. Sample rate nya minimal 2x frek tertinggi. 
DAC. 
Resolusi ADC dan DAC antara 8-32 bits
Sample ratenya 8khz-192 khz. 
CD quality audio 16 bits, 44.1 khz
Wajibnya ada 3 sambungan/kabel
1.	SCK : continuous serial clock
2.	WS word select
3.	SD : serial data
 
Src : https://espressif-docs.readthedocs-hosted.com/projects/esp-adf/en/latest/design-guide/dev-boards/board-esp32-lyrat-v4.3.html#i2s-header-jp4 

 

 
lyraT mini>>> LyraT 4.3

https://github.com/espressif/esp-adf/issues/1047 masih belum paham gimana cara solved nya
tapi nanti coba :
1.	di esp-idk/componets/driver coment si desprecated/i2s_legacy.c 
src : https://esp32.com/viewtopic.php?t=35239 

masalah yg sama dn blm solved : https://github.com/micropython/micropython/issues/13104 

8 juli 2024

Word Select (WS)
•	A logic low on WS indicates that the word currently being transferred is part of the data stream for the left audio
•	 channel; logic high on WS indicates right-channel audio.
•	To facilitate data handling on both the transmitter and the receiver side, the WS signal transitions one clock period before the completion of a data word:
 
 
ESP32 A1S..
Both the ESP32 LyraT 4.3 and ESP32-A1S are capable of handling VoIP applications, but the choice depends on your specific requirements:
•	ESP32 LyraT 4.3: Better suited if you need a more feature-rich development platform with extensive support and more built-in audio components. The LyraT 4.3's robust framework support and built-in connectors for microphones and speakers make it a more convenient choice for developing and testing VoIP applications.
•	ESP32-A1S: Better suited if you need a more compact solution and can manage with fewer GPIO pins and peripheral interfaces. The A1S might be preferable for embedded applications where space is a primary concern, but it might require more effort to set up the necessary peripherals for VoIP.
In summary, if ease of development and more built-in features are critical, the ESP32 LyraT 4.3 is the better choice. If a smaller form factor and a more minimalistic approach are desired, the ESP32-A1S would be a better fit.
12 Juli 2024
 
 

Coba pake Arduino
Referensi : https://github.com/RetepRelleum/SipMachine/blob/master/examples/voip.ino atau https://github.com/rousir/ArduinoVoip 

Bisa coba balik ke esp https://github.com/yijenlu1971/voip?tab=readme-ov-file tapi di paduin pake example biasa

https://github.com/OLIMEX/sip_phone_example/tree/master kemarin coba ini cuma masih sama masalah nya

 
Salah satu masalahnya adala pada 
CSeq 0 REGISTER karena 0 merupakan nilai yang tidak valid sehingga request akan ditolak

 

15 Juli 2024

Terdapat 2 opsi
1.	Mencari masalah driver dan library pada espressif/ esp-adf
2.	Mencari solusi untuk codingan di Arduino
Hint opsi 1 :
 
https://han-ya.blogspot.com/2021/09/esp32-audio-voip.html 

bikin schematic lyrat mini?
 
Baru bikin codec dan adc
Catetan buat laporan :
Inputs
1.	Microphone Input:
o	The ESP32 LyraT board typically has one or more built-in microphones or connectors for external microphones.
o	Analog audio signals from the microphone are captured and converted to digital format using the ES8388 audio codec.
2.	Network Input:
o	VoIP packets (e.g., RTP packets carrying compressed audio data) received from the network.
o	Control messages for call setup and management, typically using SIP.
3.	User Inputs (optional):
o	Buttons for call control (e.g., answering, hanging up).
o	Possible input from a touchscreen or other user interface elements.
Outputs
1.	Speaker Output:
o	Digital audio data is converted back to analog signals using the ES8388 codec.
o	The analog signals are output to the built-in speakers or connected external speakers.
2.	Network Output:
o	VoIP packets containing compressed audio data are sent over the network.
o	Control messages for call setup and management, using SIP.
3.	User Feedback (optional):
o	LEDs or displays to indicate call status (e.g., ringing, in call, call ended).
o	Audio feedback tones (e.g., dial tones, busy signals).
Detailed Breakdown of the VoIP System
Audio Input
1.	Microphone Capture:
o	The microphone captures the user's voice as an analog signal.
o	The ES8388 codec digitizes the analog signal to a digital audio stream.
2.	Audio Processing:
o	Digital audio data may undergo processing such as noise reduction, echo cancellation, and gain control.
o	The processed audio data is then encoded using a codec like G.711 (or other suitable codecs for VoIP).
3.	Packetization:
o	The encoded audio data is packetized into RTP (Real-time Transport Protocol) packets for transmission over the network.
Network Input
1.	Receiving RTP Packets:
o	RTP packets are received from the network containing compressed audio data.
o	These packets are depacketized to extract the encoded audio data.
2.	Decoding:
o	The compressed audio data is decoded using the appropriate codec (e.g., G.711).
o	The decoded digital audio data is ready for playback.
Audio Output
1.	Audio Playback:
o	The decoded digital audio data is sent to the ES8388 codec.
o	The ES8388 converts the digital audio data back to an analog signal.
o	The analog signal is output to the built-in speakers or external speakers.

18 Juli 2024
Integrasi radio holder Dicom RF23
-	LCD (i2c)=35627-MP arduino color lcd 
-	Rotary switch== 10 pin => PCF8574
-	Key pad (expander)
o	DI touch keys
o	DO LED
-	System pengisian charger jack di mikro
-	Batre pake 3,7 paralel 4 di buck ke 3,3v
-	PTT switch microphone
-	Headset :
o	Mic
o	Speaker
  https://www.youtube.com/watch?v=HtX2o0UQelI 
https://github.com/xreef/PCF8574_library 
Q : dari charging port ke batre, pake apa?
Q : bagaimana cara kerja pin interruptnya?
https://forum.arduino.cc/t/solved-pcf8574-daisy-chaining-interrupts/674258/3 
read 
https://forum.arduino.cc/t/connect-two-i2c-boards-at-once/919450/4
https://www.makeriot2020.com/index.php/2020/09/12/multiple-i2c-devices-on-the-same-bus-i2c-part-3/

how if, we use STM32?
 STM32F7
Src : https://community.st.com/t5/stm32-mcus-products/simple-voip-client-od-stm32l475-mcu/td-p/370640

23 juli 2024
Cicil laporan. Logbook ok, tinggal konfirmasi soal anomali tanggal
24 Juli 2024
Audiokit AI-Thinker has arrived!
Schematic : https://docs.ai-thinker.com/_media/esp32-audio-kit_v2.2_sch.pdf 
adf instalasi : https://espressif-docs.readthedocs-hosted.com/projects/esp-adf/en/latest/get-started/index.html 
 
 
Besok coba read.me nya esp32-a1s
25 Juli 2024
Kayaknya kemarin masalah instalasi di vscodenya
 
New installation!
Erornya sama aja

Dia make es388 ternyata
https://fccid.io/2AHMR-ESP32A1S/User-Manual/User-manual-4883471.pdf 
26 juli 2024
Coba di computer pak jusan
New problem! 
E (1237) MEDIA_OS: Not found right xTaskCreateRestrictedPinnedToCore. (AUD-4376) #948
E(1256) AUDIO_THREAD : Error creating RestrictedPinnedToCore input_key_service
E(1272)INPUT_KEY_SERVICE: null pointer  
Pake idf 4.4.7
Adf 2.6 hasilnya sam aaja nihil
Adf master juga sama 
Adf 2.5 baru mau coba
29 juli 2024
Coba pake versi adf dan idf yg sama kayak ref.
ESP-IDF Release v4.1.2
ESP-ADF Release v2.3

 
 
Saat set target ga bisa
30 juli 2024
Install idf 5.3 di laptop dan adf master
Pas genti board config malah eror banyak yg sebelumnya Cuma 1 ini 
 
Dan ga bisa pencet button di boardnya

Tapi jadinya:
 
Tes board pake hello world bisa
  
Update progress, coba cari micro atau alternatif board lain
31 Juli 2024
Ini yg keliatannya gampang : https://www.instructables.com/How-to-make-VoIP-calls-from-Raspberry-Pi/ 
Buat referensi dengan framework lain : https://www.linphone.org/technical-corner/linphone 
raspi 3 b+ : https://guillaume.nibert.fr/voip-asterisk-rpi-ipphone-project/ 
incredible pbx : https://nerdvittles.com/the-definitive-voip-quickstart-guide-incredible-pbx-for-the-raspberry-pi/ 
baik power raspinya gimana?
 
Ethernetnya?

Dari hasil implementasi dan pengujian sistem yang telah dilakukan, dapat disimpulkan bahwa cara kerja VoIP yaitu data suara diubah menjadi kode digital dan dialirkan melalui jaringan yang mengirimkan paket - paket data

Beberapa opsi untuk raspi seperti 
Raspberry Pi 4 Model B
Raspberry Pi 3 Model B+
Raspberry pi zero 2 W

Memory kecil ga masalah harusnya minimum 512mb, amannya 2gb

As stated in a previous answer to this thread, the pi doesn't have a sound input or microphone.
You either need to connect via bluetooth or use an USB audio card
Untuk masalah suara : https://forums.raspberrypi.com/viewtopic.php?t=170160 

21 agustus 2024
  
Udh bisaaaaaaaa

REGISTER
 
Error : 
I (3307) AUDIO_THREAD: The DEC_mp3 task allocate stack on external memory
E (3307) TONE_PARTITION: Not flash tone partition
I (3315) MP3_DECODER: MP3 opened
I (3315) ESP_AUDIO_TASK: Blocking play until received AEL_MSG_CMD_REPORT_MUSIC_INFO
E (3324) AUDIO_ELEMENT: [IN_flash] AEL_STATUS_ERROR_OPEN,-1
E (3338) TONE_PARTITION: tone_partition.c:205 (tone_partition_deinit): Got NULL Pointer
I (3339) ESP_AUDIO_TASK: Recv Element[IN_flash-0x3f806b0c] MSG,type:20000,cmd:8,len:4,status:ESP_ERR_AUDIO_OPEN
E (3347) MP3_DECODER: Failed to read audio data (line 129)
E (3358) ESP_AUDIO_TASK: Got element[IN_flash] error:ESP_ERR_AUDIO_OPEN, stop pipeline[0]
Register, call in, hang up done
Problem : suara g amasuk
coba : pake asterisk servernya dan pake wireshark
coba idf 4.4 + adf master di vscode

22 Agustus 2024
Note : kemarin pake python yg 2. Sekian
Ver phyton hrsnya g amasalah
Ini udh bisa telfon ke softphone, dengan cara masukin id nya ke button
Masalahny amasih sama, ga ada suara

"# Doc-Of-KerjaPraktik" 
