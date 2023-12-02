# Lessons Learned 

## Team Memeber 1: Raymond Mule

### Reflect on the project, both technical and organizational. What went well? What didn’t go well?
What went well during this project was the actual designing and building of the prototype. 
The detail designs were tough, but they helped me understand my subsystem very well, so when 
it came to actually constructing and combining my subsystem with my fellow teammates' subsystems, 
it was rather easy. The testing of the prototype also went well. It was fun to see our system
actually be able to measure an individual’s heart and respiratory rate and then continue to improve
it to make the system more accurate. What didn’t go well was the reports we had to write in the
Capstone 1 portion of this course. The team was stumped at how to find a solution to our project’s
problem, and once we had a general idea of the solution, it was even harder to create a specific 
solution that would fulfill the team’s needs and constraints. The team also did not have enough experience
writing the reports such as the project proposal and the conceptual design. This led to those reports
not having sufficient information to convey to the reader. 
### What unanticipated problems occurred?
During this project, the team ran into multiple problems. The first problem occurred while writing the
detail design for the heartbeat and respiratory system. The search for finding a radar that would fit
within our needs and constraints was very hard to find, and a lot of time was wasted trying to find said radar.
The next problem occurred while the team was trying to construct the minimally functional prototype.
The Jetson Nano that was originally going to be used as the computing subsystem could not communicate with 
analog to digital converter. The team thought this was an issue that could be fixed by configuring the Jetson
Nano, but after three weeks of trying to solve this problem, the team caved in and purchased a Raspberry Pi to
act as the computing subsystem instead. The other problem that we ran into is that the analog to digital converter 
that we were using was somehow broken. This may have been the reason why it would not communicate with the Jetson 
Nano, but the team had already purchased the Raspberry Pi at this point. Luckily the team was sent two analog to 
digital converters, so we simply replaced the old analog to digital converter with the new one and it worked fine. 
Another problem that we ran into is that we could not get the Raspberry Pi to interact with the speaker for the
voice activity detection system. AFter trying numerous libraries and different codes using Python, the team ran out 
of time and had to exclude the speaker from the project.
### What would you do differently if you were to do it over again?
If I were to do this project again, I would definitely spend more time doing research for the project proposal,
conceptual design, and detail design. Having more information would have greatly helped in the writing of these
reports and made it much easier to convey all of the necessary information to the reader.
### What “best practices” have you identified?
The best practices that I have identified is definitely communication. The team easily communicated with one
another allowing most of the project to run smoothly. Each team member clearly expressed their ideas on how 
to solve a problem when it occurred, and the rest of the teammates listened to see if the proposed solution 
could actually work. The good communication skills also led to the team having a great friendship with one another, 
which helped the project be more enjoyable.
### What words of wisdom would you pass on to future students?
The words of wisdom I would pass down to future students is that communication is key. Communication with your
professor, advisor, ECE office staff, and your teammates will make the project run far more smoothly than if you 
did not practice good communication. Good communication skills also help you grow closer to your teammates which 
makes the project a lot more enjoyable and rewarding to complete.
### What new knowledge or skills did you acquire throughout capstone.
The main knowledge that I have acquired through this project is definitely LoRa transceivers since that is the
transceiver that I used to achieve the wireless communication subsystem for this project. I was also able to
learn more about these transceivers due to the technical presentation that I had done over them. I also learned 
about Python by working closely with Logan who designed the computing subsystem and helped me implement my subsystem
with his. I also learned a lot about radars since that was the main point of our project. Andrei, who was the main 
designer of the heartbeat and respiratory subsystem that used the radar, shared a lot of his knowledge with me so I 
could better understand the radar that we were working with and what we were trying to accomplish. I also learned a 
lot about working together as a team. In previous classes, I had only worked in groups of two, maybe three, so getting 
the chance to work in a team with four other people was really interesting. It was also interesting to hear all of
their thoughts on how to solve problems that we had run into. Overall, this course was a very enriching experience.

&nbsp;    
## Team Memeber 2: Michael West

### Reflect on the project, both technical and organizational. What went well? What didn’t go well?
Signoffs were definitely an issue later on last semester and earlier on this semester. It was not clear what 
was expected of us when it came to those, and took a long process of trial and error to finally not only get
approved, but to have them considered complete. Parts also took longer than anticipated to get in. However, 
once we had all of our signoffs approved and all of our parts in, and the proper replacement parts also ordered, 
we were surprised at how quickly we were able to work together to get this system minimally functional. We did 
really well working as a team. We all respected each others’ contributions, knew when to ask each other for help, 
and knew each other member’s area of expertise. The final Capstone presentation and expo also went exceptionally well.
### What unanticipated problems occurred?
When we finally got our Jetson Nano in, we were shocked to learn how limited it was based on the way it came 
programmed from the supplier. We quickly found out that it was not feasible to program our computing subsystem onto 
this part, and we ended up needing to personally order a Raspberry Pi for ourselves. Then, due to some human error
on someone’s part, the heartbeat and respiratory radar was shorted just as we were planning on getting experimental 
data from the system. We had to wait over a week for the replacement part to come in before we were able to get said 
measurements.
### What would you do differently if you were to do it over again?
Most of what went wrong were problems that we couldn’t have possibly seen coming. I would not do much differently
from how we worked on the project, I feel a second run would just be more efficient because we would now know to 
order a Raspberry Pi instead of a Jetson Nano, and we would already know the information on specifics of this project
that we had to take the time to learn to build it the first time.
### What “best practices” have you identified?
Working as a member of a team is honestly the most integral best practice. Making sure to communicate clearly 
and precisely with honesty and integrity, as well as getting to know your teammates such that the project can be
built utilizing the strengths of each individual member at their fullest capabilities. Not being afraid to ask
for help is another major part of that. This project consisted of multiple individual subsystems interacting with 
one another, so every member needed to at least know what each subsystem took as an input, did with said input, 
and what it outputted. Paying close attention to detail when dealing with connecting a power system for example, 
as well as being vigilant on making sure one is able to recall and understand the precise mechanics behind their 
subsystem for each member is also a best practice I can identify.
### What words of wisdom would you pass on to future students?
Choose a project with less medical science behind it than this project and be sure to understand your teammates’
strengths such that they can be utilized for the best of the project. Do not be afraid to ask for help, and do not
be afraid to get to know your teammates.
### What new knowledge or skills did you acquire throughout capstone.
I strengthened my communication skills significantly through this class, sharpened up some skills relating to Digital
Signal Processing, and learned how to program in Python from scratch. I learned a lot about it from Logan in particular.
This was also a great opportunity to practice my programming skills in general. I also practiced my presentation skills 
thanks to this class.

&nbsp;  
## Team Memeber 3: Russell Gadd

### Reflect on the project, both technical and organizational. What went well? What didn’t go well?
Sign-offs took an exceptional amount of time. The time to get feedback and the time to fix the issues took
longer than what we anticipated. Each team member working on a separate subsystem while collaborating extensively 
worked very well.
### What unanticipated problems occurred?
Having to switch our processing unit from a Jetson Nano to a Raspberry Pi was an unanticipated problem. Having 
to order another radar module because we shorted the first one was an unanticipated problem.
### What would you do differently if you were to do it over again?
I would have pushed to get everything signed off and ordered by the end of Capstone I so that we would have
had more time to build and test our design during Capstone II.
### What “best practices” have you identified?
Organization with material and tracking data throughout all experiments are good practices.
### What words of wisdom would you pass on to future students?
Everything is negotiable. Be sure to communicate well with your teammates but also with your supervisor. 
### What new knowledge or skills did you acquire throughout capstone.
Through Capstone I have learned about radars, LoRa transceivers, and a lot about DC-DC converters just from my
teammates and through my own research as we worked to complete our project. 

&nbsp;  
## Team Memeber 4: Andrei Matei

### Reflect on the project, both technical and organizational. What went well? What didn’t go well?
For the overall project the teamwork and physical system building went well. The biggest issue that didn’t 
go well is the timing of all the things we needed to accomplish. Signoffs took way too long so we only had 
a month and week to build and test our system. This meant that there wasn’t enough time to complete all the tests 
we wanted for each system. Because of the teamwork we wers till able to have a working system, it just only has
been tested in ideal situations. 
### What unanticipated problems occurred?
The biggest unanticipated problem was the fact that our original computing system wasn’t compatible with our ADC system.
This caused us to waste two weeks of time to manually try and set the GPIO pins of the Jetson Nano only to find that 
none of the solutions would allow us to change the 40 pin header to set the SPI pins needed. This meant we had to swap 
to a whole new computing system. Thankfully the Raspberry Pi worked perfectly and still matched out constraints. The
second unanticipated problem was the speaker system not working. This again was an issue with the internal computing 
system, something that seemed straightforward would not play any sound running our program. Lesson learned that its the 
small things with the configuration of the system that end up being the biggest problem.  
### What would you do differently if you were to do it over again?
Work on a timeline schedule and stick to it closer. Not just the one that's required, but one that the team 
understands and follows, a realistic schedule of completing things, maybe even one that sets the schedule for the week. 
This way everything can be done more efficiently.
### What “best practices” have you identified?
One of the “best practices” would be to communicate everything with your team but also with your professor. Everyone 
being on the same page helps a lot with getting things done rather than arguing how to get those things done. It also 
allows for the project goals to match between all team members. Another practice is to be honest with your issues and 
results. If something doesn’t work that’s ok, if something unexpected happens that’s ok too. But everyone should be 
aware of all those things. Lying and pretending that something is ok when is not helps no one. And the last practice 
is to do your part. No one wants to do the whole project or another members work. Work as a team and everyone do there 
part and the results will follow. 
### What words of wisdom would you pass on to future students?
Pick a good team and a project that you will enjoy. This class will take up a lot of your time, make it one that
you won’t hate. Manage your time wisely and don’t worry it’ll all be over soon. 
### What new knowledge or skills did you acquire throughout capstone.
I learned a little more about coding in python, a lot about how radars function, and a little more about the structure
of how a project works from formation to implementation. The whole system was coded in python so I got a chance to 
understand a little more about the syntax and the operation of python. Through the research for this project I also 
learned a lot about how a radar actually works and the capabilities for applications of radars. And finally through 
all the proposals, conceptual designs, and detail designs, I also got a look into how a full engineering project works.

&nbsp;  
## Team Memeber 5: Logan Newport

### Reflect on the project, both technical and organizational. What went well? What didn’t go well?
The project went well overall but it did come with some unintended road blocks along the way. As far as everything 
organizational, the group worked great together. The technical side of things presented a few setbacks including having
to change the development board of the computing subsystem from a Jetson Nano to a Raspberry Pi, and also having to
purchase another radar due to shorting VCC to GND. 
### What unanticipated problems occurred?
As stated above, we had to change the development board and purchase a new radar. 
### What would you do differently if you were to do it over again?
I wish that signoffs would’ve been done quicker so I would’ve had more time for the building and testing phase.
### What “best practices” have you identified?
Its a good practice to get in front of deadlines instead of always trying to play catch up.
### What words of wisdom would you pass on to future students?
Communication is so important, always collaborate with the intent for designs to be modular so implementation is seamless.
### What new knowledge or skills did you acquire throughout capstone.
My presentation and teamwork skills improved significantly due to capstone.

