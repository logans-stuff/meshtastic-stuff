# Meshtastic Information

Repository of Meshtastic information I have gathered.

## Products that have been confirmed to work

- Some beefy antennas ([source](https://github.com/RicInNewMexico/Meshtastic-Antenna-Reports)) (NEED RP-SMA MALE) [AliExpress Link](https://a.aliexpress.com/_mNzvdYQ)
- Anything from RCMall seems good [AliExpress Link](https://a.aliexpress.com/_mq4kHWS)
- Batteries (MakerFocus seems to be the choice) [Amazon Link](https://a.co/d/fHV2kxH)
- Verified Pi hat Waveshare SX1262 [Amazon Link](https://www.amazon.com/dp/B0C61VK6WQ)
- Decent omni-directional urban setup:
  - [Antenna](https://store.rokland.com/products/5-8-dbi-n-male-omni-outdoor-915-mhz-antenna-large-profile-32-height-for-helium-rak-miner-2-nebra-indoor-bobcat?currency=USD)
  - [Lightning Protector](https://store.rokland.com/products/alfa-alr6-n-male-n-female-lightning-protector-for-antennas-0-6-ghz-wi-fi)
  - [Antenna Extension Coaxial Cable](https://store.rokland.com/products/20-ft-antenna-extension-coaxial-cable-rp-sma-male-to-n-female-bulkhead-rfc-400-low-loss?variant=39405156008019&currency=USD)
- Printable case: [Printables.com](https://www.printables.com/model/741974-h1-case-for-heltec-v3-running-meshtastic) | [Etsy](https://www.etsy.com/listing/1653262584/h1-case-for-heltec-v3-running-meshtastic)

## Linux Information 

- [Documentation](https://docs.google.com/document/d/17LW4ExkG6xVFnusVBMaDMA08kmZfyHiPbi8vjLpmLAs/edit) (Mirror PDF is in the repo.)
- Working on a PI3 + Waveshare SX1262 [Amazon Link](https://www.amazon.com/dp/B0C61VK6WQ)

Two working distros I've tested:
- Ubuntu Server LTS 22.04
- Raspbian 64 bit Bookworm

### Bullseye Notes
```bash
sudo raspi-config
```

Enable I2C + SPI + Serial Port.

We like to cause problems and run bleeding edge, mainly because I'm looking for web UI support on the PI. 

```bash
wget https://nightly.link/meshtastic/firmware/workflows/main_matrix/master/artifact-deb.zip
```

```bash
unzip artifact-deb.zip
sudo apt install ./meshtasticd_2.* 
```

Standalone start command:

```bash
sudo meshtasticd -d /home/pi/
```

Master meshtasticd configuration directory:

```bash
/etc/meshtasticd/config.yaml
```

Managing via CLI:

```bash
sudo apt-get install python3-pip
pip3 install --upgrade pytap2 --no-binary :all: --force-reinstall
pip3 install --upgrade meshtastic --no-binary :all: --force-reinstall
```

Ensure to use `--host localhost` on all commands. For example:

```bash
meshtastic --host localhost --nodes
```
<img width="959" alt="itworks" src="https://github.com/LoganNehrbass/meshtastic-stuff/assets/39987450/ddab039c-7b09-4699-97e3-d6fa5e19ed4b">
