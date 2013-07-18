ASTROCAMS
=========

ASTROCAMS - providing CAMS users a way to easily re-calibrate their camera through cross-platform data manipulation.
NOTE: Please read the Wiki for installation instructions!

Introduction
============
Welcome to ASTROCAMS! I'm glad you decided to use my software to help facilitate your CAMS camera calibration process. I highly suggest you read over this Wiki before operating ASTROCAMS, as ASTROCAMS cannot function by itself - it requires additional resources the user must download and manually install.
How ASTROCAMS works

ASTROCAMS acts as a middle man software that will transfer data between the Windows operating system, where the user will submit FF data for calibration and the solution software that runs on a Linux operating system in real time.

These FF files should be generated before using ASTROCAMS. Generally, the FF files contain data relevant to a night capture of the sky. When ASTROCAMS calls on an executable to pull a raw .jpg file (a picture that contains only the stars of the captured photo), it is then sent over to Astrometry through the use of a shared folder provided by the Virtual Machine.

On the Linux side, a Bash script (startAstrocams) will constantly check the shared folder for any new data to process. When it detects a new file, startAstrocams will then execute the solution software called Astrometry. Astrometry will then compare the inputted file with its virtual star catalogs and then generate an annotated picture. This picture is then automatically sent back to ASTROCAMS (along with other solution data, detailed below) and then presented to the user.
Expected Output

ASTROCAMS will not output a solution in a CAL format CAMS (Cameras for All-Sky Meteor Surveillance) users are familiar to. ASTROCAMS will output information (should the user decide to save the information or copy it to the system clipboard) such as the following:

    Center (RA, Dec)
    Size
    Radius
    Pixel Scale
    Orientation 

ASTROCAMS will then present the user with an annotated picture similar to the following picture: http://nova.astrometry.net/user_images/31577#annotated.

Should the user decide to save the calibration data as a text file, the file will be formatted like the example shown below:

    ASTROMETRIC SOLUTION DATA OF [FF file name]
    Saved and solved on [date FF file was submitted and solved on]
    //ASTROCAMS - BUILD [build number] //Astrometry - 21399
    ===============================================================
    Center (RA, Dec): (24,761, 64.036)
    Size: (29.97 x 22.17 deg)
    Radius: 37.279 deg
    Pixel Scale: 168.648 arcsec/pixel
    Orientation: Up is -13.814 E of N

Required downloads
==================
Please see the installation page for information on how to install the following pieces of software.

    Oracle VirtualBox? Virtual Machine Software
    Ubuntu (12.03 or higher) ISO download
    Astrometry software made available at www.astrometry.net.
        Index files 4010 to 4019. Contact the authors of www.astrometry.net for permission. 
