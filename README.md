# Code Snippet - F_VN_FitLine
What is a code snippet? These are mini blocks of code which help me to remember and reuse parts of Infosys.  
These are not "Wow" level examples.  They are just ultra simple, copy paste code.  But as always, I like to share.

## Disclaimer
This is a personal guide not a peer reviewed journal or a sponsored publication. We make
no representations as to accuracy, completeness, correctness, suitability, or validity of any
information and will not be liable for any errors, omissions, or delays in this information or any
losses injuries, or damages arising from its display or use. All information is provided on an as
is basis. It is the reader’s responsibility to verify their own facts.

The views and opinions expressed in this guide are those of the authors and do not
necessarily reflect the official policy or position of any other agency, organization, employer or
company. Assumptions made in the analysis are not reflective of the position of any entity
other than the author(s) and, since we are critically thinking human beings, these views are
always subject to change, revision, and rethinking at any time. Please do not hold us to them
in perpetuity.

## Overview 
This is a code snippet example of F_VN_FitLine to make a line between to points added to a container.

## Screenshot
![image](./docs/images/Screenshot.png)

## Code Snippets

```
PROGRAM MAIN
VAR
	
	myImage : ITcVnImage;
	myDisplayableImage   : ITcVnDisplayableImage;
	point1 : TcVnPoint2_REAL := [100, 200];
	point2 : TcVnPoint2_REAL := [400, 300];
	points : ITcVnContainer;
	resultingLine : TcVnVector4_LREAL;
	hr : HRESULT;
	aColorWhite : TcVnVector4_LREAL := [255, 255, 255];
	aColorGreen : TcVnVector4_LREAL := [0, 175, 0];
	aColorBlue : TcVnVector4_LREAL := [0, 0, 255];
	aColorRed : TcVnVector4_LREAL := [255, 0, 0];
	
END_VAR
```
```
    hr := F_VN_CreateImageAndSetPixels(myImage,500,500,ETcVnElementType.TCVN_ET_USINT,3,aColorWhite,hr);

    hr := F_VN_DrawPoint(REAL_TO_UDINT(point1[0]),REAL_TO_UDINT(point1[1]),myImage,TCVN_DS_PLUS,aColorRed,hr);
    hr := F_VN_DrawPoint(REAL_TO_UDINT(point2[0]),REAL_TO_UDINT(point2[1]),myImage,TCVN_DS_PLUS,aColorBlue,hr);

    hr := F_VN_CreateContainer(points,ContainerType_Vector_TcVnPoint2_REAL,0,hr);

    hr := F_VN_InsertIntoContainer_TcVnPoint2_REAL(point1,points,0,hr);
    hr := F_VN_InsertIntoContainer_TcVnPoint2_REAL(point2,points,0,hr);

    hr := F_VN_FitLine(points,resultingLine,hr);
    hr := F_VN_DrawLine_TcVnVector4_LREAL(resultingLine, myImage, aColorGreen, 1, hr);

    hr := F_VN_TransformIntoDisplayableImage(myImage, myDisplayableImage, S_OK);
```

## Versions
* TcXaeShell 3.1.4024.22
* TwinCAT Vision 4.0.2.13

## Need more help?
Please visit http://beckhoff.com/ for further guides
