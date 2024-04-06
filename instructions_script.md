---
layout: howto
title: Instructions
permalink: /howto/

has_toc: true
nav_order: 1

---

# Setting Up a Raspberry Pi Headless (SSH) Connection
{: .no_toc }

By: Connor Robinson, Aidan Costello, Thomas Elpers, Abel Lu

By following these steps, you’ll be able to connect to your Raspberry Pi headless using SSH and Nmap. 🎩🍓

<details open markdown="block">
  <summary>
    Table of contents
  </summary>
  {: .text-delta }
 - TOC
{:toc}
</details>

**Walkthrough video (Windows 11):**

<iframe width="560" height="315" src="https://www.youtube.com/embed/Zan5VUIiTc4?si=9vJSQe0o1E1YR7QW" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>


## 1. Get the Raspberry Pi Imager:

 - Visit the official [*Raspberry Pi website*](https://www.raspberrypi.com/software/) or the [*GitHub repository*](https://github.com/raspberrypi/rpi-imager) to download the Raspberry Pi Imager tool.

 - Choose the version suitable for your operating system (Windows, macOS, or Linux).

## 2. Download the Correct OS for the Pi:

 - Launch the Raspberry Pi Imager tool.

 - Click *Choose Device* and select your Raspberry Pi model from the list of devices

    <details closed markdown="block">
    <summary>
        Show image
    </summary>
    {: .text-delta }
    ![select pi]()
    {: .text-delta }
    </details>
 
 - Click *Choose OS* and select the appropriate operating system for your Raspberry Pi. For headless setup (without a graphical user interface), consider using **Raspberry Pi OS Lite**.

    <details closed markdown="block">
    <summary>
        Show image
    </summary>
    {: .text-delta }
    ![select os]()
    {: .text-delta }
    </details>

 - Click *Choose Storage* and select your microSD card.

    {: .warning }
    > Flashing an OS will replace **EVERTHING** on the microSD card. Be sure to transfer any important files first!

    <details closed markdown="block">
    <summary>
        Show image
    </summary>
    {: .text-delta }
    ![prompts]()
    {: .text-delta }
    </details>

## 3. Configure Settings in the Imager:

**Before writing the OS image to the microSD card, configure Wi-Fi and enable SSH:**

1. Click on *"Choose OS"* and select the OS image you've downloaded.

    <details closed markdown="block">
    <summary>
        Show image
    </summary>
    {: .text-delta }
    ![choose os]()
    {: .text-delta }
    </details>

1. Click on *"Choose SD Card"* and select your microSD card.

1. Click on *"Wireless Network"* and enter your Wi-Fi credentials.

1. Enable SSH by clicking on *"Interfacing Options"* and checking the "SSH" option.

1. Click on *"Write"* to flash the OS image to the microSD card with the configured settings.



## 4. Download the CLI Version of Nmap:

 - Visit the official Nmap website and download the command-line version suitable for your operating system.
 - Follow the installation instructions provided for your platform.

## 5. Open Your Computer's CLI:

{% tabs NAME %}

{% tab NAME Windows %}

Open the Command Prompt (search for "cmd" in the Start menu).

{% endtab %}

{% tab NAME macOS %}

Open the Terminal application (you can find it in the Utilities folder within Applications).

{% endtab %}

{% endtabs %}

## 6. Run the Correct Nmap Scan:

 - Use Nmap to scan your local network for devices:

```sh
nmap -sn 192.168.1.0/24
```
 - Replace `192.168.1.0/24` with your actual network range.

## 7. Decipher Which Open Port is Your Raspberry Pi:

 - Look for an open SSH port (default is port 22) associated with a device in the scan results. Note down the IP address of the Raspberry Pi.

## 8. SSH into Your Raspberry Pi:

{% tabs ssh %}

{% tab ssh Windows %}

You'll need an SSH client like [PuTTY](https://www.putty.org/).

Open PuTTY.

Enter the Raspberry Pi's IP address and click "Open."

Log in with the username (pi) and password (default is raspberry).

{% endtab %}

{% tab ssh macOS %}

Open the Terminal.

Use SSH to connect to your Raspberry Pi:

```sh
ssh pi@\<RaspberryPi_IP\>
```
 - Replace \<RaspberryPi_IP\> with the IP address you noted down.

{% endtab %}


{% endtabs %}

## 9. Make a New File:

 - Once connected via SSH, create a new file with the following command

```sh
touch hello_world.txt
```

## 10. Exit from Raspberry Pi:

 - To exit from the Raspberry Pi terminal, type:

```sh
exit
```

## 11. Test the Connection Again:

 - Repeat step 8 to SSH into your Raspberry Pi and ensure you can still connect successfully.

 - Enter the following command:

```sh
ls -la
```

 - You should see a list of files including the `hello_world.txt` file we made earlier.

Now you have access to your Raspberry Pi using SSH and Nmap! 🎩🍓