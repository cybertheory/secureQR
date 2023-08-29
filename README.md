# secureQR

![DALL·E 2023-08-29 11 59 27 - evil qr code with red background hyperrealistic style](https://github.com/cybertheory/secureQR/assets/27149047/44f75b0b-f057-4d28-a0af-8bee6aed0074)


## Attack Surface

QR codes are widely used as digital waypoints in everyday life. They give real world context to digital content and are very powerful marketing, distribution, and analytics tools. The problem is that QR codes are often used to inject malicious content onto users smartphones and even computers. This repo aims to design and provide a replicable standard solution to creating malware secure QR codes.

## How it works

secureQR is the TSA precheck for QR codes. 

Before any device redirects a user using the QR protocol we encourage developers to check with the secureQR service to see if a QR code exists in the registry (meaning its trusted.) 

If the QR doesn't exist developers should warn users of this and provide the option to wait a few minutes for the service to check the code (or to continue on to the content).

The secureQR service will resolve the QR code server side and run checks to determine if the content is safe for the end user.

The aim is to provide checks for all types of QR content (Mailcious URLs, Malencoded Files, Text Based Exploits, etc.)

## How to use

Typically secureQR will assign a QRcode generator a particular UUID to encode QRCode content with so it is unreadable unless parsed through the service. This is optional for the person generating, due to the fact that this nessicates an internet connection for the end user, which is not always available. 

This proccess will ensure that most QR codes generated with popular generators are already in the registry, speeding up the proccess for the end user.

To make this as easy as possible, secureQR has only one API end point. This can be used on generation and is required after scan:

### CheckQRRegistry Endpoint (POST)
This endpoints validates if the given QR code is in the registry. If it isn't, False is returned and the user should be warned, else True is returned with a safety check field. If safety check field is True the user should continue, if it is false the user should be warned of this or even stopped. 

Endpoint URL: TBA

Field: qrcode
