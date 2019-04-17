# Artificial muscles stimulation with Arduino

## Introduction:

Years ago, I discovered Arduino during a 4 months project. I was amazed by the
technology and all the possibilities it offers. Through this post I’d like to share this personal
experience in Arduino and more generally embedded technology. I hope that sharing this
experience today will give you an interest in it as much as I have.

## Context:

In 2014, I joined a small French medical technologies research company. The project
that I worked on was called the “Myo-Neuro Simulator”. This device was initially designed in
a neurologic laboratory in Moscow, to artificially contract muscles by electric impulses.
The purpose of the device was to give the ability to a patient to walk after being
partially-paralyzed. This experiment has been proven to be working in Moscow on children
with Cerebral Palsy (Weaken muscles pathology) for several sessions of 20 minutes.
Interested by the technology, the CSTL (Scientific and Technological Cooperation of
Lorraine) contacted the company to adapt the Russian technology to European medical
standards and norms.
By the time the project was assigned, a clinic in Nancy showed interest in the project and
was expecting a functional device within the next months to perform clinical trials on
rehabilitating patients.
The first phase of the project was to study the actual device to understand its behavior and
correct what couldn’t fit into the European medical norms.


## Studying the product:

After receiving a prototype, an hardware engineer studied the device and find out that
the original flow of impulses could be dangerous for the patient. The Russian device actually
used to send modular charged impulses regularly.
![alt text](https://github.com/guiduca/BlogPost/blob/master/impulsePos.png "Image Impulse")
This setup could produce burns of the cutaneous fabric (the tissue located between
skin and muscle) by overcharging it on tension. Therefore, we modified this signal by
sending a negative impulse after each positive impulse to lower the tensions in muscles,
shaping the signal like this:
![alt text](https://github.com/guiduca/BlogPost/blob/master/impulseNeg.png "Image Impulse")
These modification led us to change the whole device by replacing the actual
firmware with a brand new microcontroller.
After studying several technologies, we ended up picking an “Arduino Due”, a
microcontroller card which we could reprogram using its own language based on C and C++.


## Using Arduino:

Programming a microcontroller enables to create a link between the hardware and
the software. Basically, the entry and the result of the program are made through analogical
inputs and outputs (while the program itself is digital).
On the entry side, elements such as a potentiometer can be added to tune the signal.
Doing so allows you to drive the analogue signal that your binary program will receive. At the
other end, you can plug an component that allows monitoring the activity such as a LED.
One specific constraint to microcontroller is that the program runs in an infinite loop
meaning that once the program is launched, you cannot stop it. It is as though the program
is constantly in a “listening mode,” waiting for any analogue input that could come at any
time. It doesn’t have the option to end like other programs usually do.
There is also a “communication input” on the card where any communication device,
a bluetooth receiver for example, can be plugged to feed the microcontroller with
information. This input can receive more details than any switch could give. This comes in
handy when setting up the parameters of a stimulation session on the device.
As we were changing the firmware, with the agreement of the clinic, we decided to
make a better use of the potential of the microcontroller by giving it an upgrade.

## Our Device:

As an upgrade to the initial device design, we added an angle sensor. The purpose
of this sensor was to calculate the walking cycle of patients. By plugging it on his valid knee,
the Arduino could evaluate his walking cycle, and stimulate his calf and thigh to reproduce
this cycle on his partially paralyzed leg.
After discussing with clinicians, and with the constraints of the infinite loop as core
function, we decided to setup 3 different modes to manage different uses of the product:

1. Rest Mode : The device is just listening, waiting to receive information from the
    analogical inputs


2. Test Mode: The device sends a flow of impulse during a second; this mode is used to
    gauge the strength of the impulse to adapt it to the patient
3. Stimulation Mode: This mod is the most complex one; it needs several parameters
    such as the strength of the impulses (previously determined using the same device in
    Test Mode) and the time of the session (20 minutes by default)
    It’s easily possible to change the device’s state and impulse strength through the
bluetooth receiver connected to the card.
In the end, the prototype have been tested in a local clinic on a patient who’ve been partially
paralyzed on half of his body after a stroke. The device successfully worked and has allowed
to foresee much more possibilities in improving patients’ life.

## Conclusion:

By the end of this project, I was amazed by the ease of use of a technology that has
a great potential. This experience, to me, concluded on the proof that controlling physical
elements with algorithms give us endless possibilities.


It also shown that with simple and easily accessible technologies and components,
such as Arduino hardware and components, we can somehow change the world and make it
better.