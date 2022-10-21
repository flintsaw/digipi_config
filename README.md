# digipi_config
Reminder for custom adjustments to DigiPi hotspot

Flash fresh DigiPi sd card

Initialize settings per normal process

sudo remount

Make USB soundcard default
  sudo nano /usr/share/alsa/alsa.conf
    defaults.ctl.card 1
    defaults.pcm.card 1

Adjust sound levels in Alsamixer
  Speaker 70
   Microphone CAPTURE 24

Edit Direwolf to use USB soundcard
  sudo nano direwolf.tnc.conf
    Uncomment "PTT GPIO 12"
    Uncomment USB Soundcard
      change plughw to hw

Change linpac to 300baud
  sudo nano linpac.sh
  edit "TNC is not active. Starting 1200baud TNC" to say 300 baud
  edit sudo systemctl start tnc300b

___NEED TO CREATE STARTUP SCRIPT
  kill default TNC and APRS igate
  sudo direwolf -q -c direwolf.tnc300b.conf
  sudo bash linpac.sh

Save Configs

Reboot
