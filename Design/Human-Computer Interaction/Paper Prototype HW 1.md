Name: Fabrizio Fonseca
Date: 9/8/2026

> I would be willing to have my work shown with my name to the entire class.

## Initial Storyboard
![[storyboard.jpg]]

Inspired by gas station kiosks. I don't have any sharpies or thick markers, so I instead just wrote really small, like thumbnail size with a dull pencil.

Important notes:
- On the title screen, START doesn't need to be pressed to begin interaction
	- Package can just be placed on scale
- Extended screens are *scrollable*, using a touch screen
- Expected that there is either a digital/physical keyboard handled by the OS
- Expected that a PIN pad is used to handle credit transaction
	- Expected that cash is not an option
		- Similar to a self-checkout or gas station kiosk
- Expected that a shipping label is printed at end of interaction

## Title Screen![[Title.jpg]]

Fairly self explanatory. Centered logo/title in screen to denote the device usage.

## Scale "Load"![[Scale Wait.jpg]]
In my experience, scales take a little while to get a consistent number. Ideally, the scale would have a little animation to show that the kiosk is weighing the package.

If the user removes the package in the middle of weighing, it will buffer for a while and then return to the title screen.

## Scale Success![[3 KG.jpg]]
Shows confirmation that the weighing is finished while also displaying package weight.

## Address Selection![[Address Select.jpg]]
I don't have the brightest idea of the input interfaces on this kiosk. However, I'm going to assume that there is some keyboard interface built within an OS level and I don't have to create a digital touch keyboard myself.

Important notes:
- Back button appears here
	- Pressing back here will go back to weighing section/cancel interaction
- Required fields are marked with a star/asterisk
	- Would need to change ZIP/State depending on the country
- Right panel is scrollable
	- Would be done through touch

## Shipping Selection
![[Shipping Select.jpg]]

Simple 3 option shipping method selection.

Notes:
- Back button takes user to Address selection screen

## Confirmation
![[Confirm.jpg]]

Confirm shipping details.
Basically shows all the information from the previous sections here.

Notes:
- Back button returns to the shipping method selection screen
	- I don't know why I didn't include it here, but there should also be an `edit` button near the shipping method selection
- Selecting a section's `edit` button will go to back to that screen.
	- I can't think of a clean way to quickly return to the confirmation screen, but it should be fine since the shipping price would change with an address change
- Scrollable panel
	- Center panel is scrollable

## Payment
![[Payment.jpg]]Self explanatory.
Expected that a separate PIN pad handles the credit transaction (similar to a self checkout).
Also expected that the kiosk only accepts card, no cash (like a gas station).

## Interaction End Screen
![[printing label.jpg]]Confirmation screen that shows a checkmark showing payment is complete.

Notes:
- Label will begin printing as soon as this is shown
	- Physical movement/sound should alert user
- Will return to title screen shortly after the label is finished printing