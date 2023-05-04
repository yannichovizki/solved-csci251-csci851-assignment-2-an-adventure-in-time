Download Link: https://assignmentchef.com/product/solved-csci251-csci851-assignment-2-an-adventure-in-time
<br>
This assignment is to be implemented using object oriented programming. It involves implementing a simulation of an adventure in time, tracing the history of some artifacts.

In addition to providing code you need to.

<h1>General notes</h1>

These are some general rules about what you should and shouldn’t do.

<ol>

 <li>Your assignment should be sensibly organised with the same kind of expectations in this area asassignment one, although you may reasonably have more files for this assignment. No memory leaks etc. too.</li>

 <li><strong>Other than the initial command line input, the program should run without user input. In particular this means there shouldn’t be pauses waiting for the user to press a key.</strong></li>

 <li><strong>There shouldn’t be pauses generally, please don’t use sleep!</strong></li>

 <li>Your code must compile on Banshee with the compilation instructions you provide in txt. If it doesn’t you will likely receive zero for the coding part of the assignment.</li>

 <li>You have to use classes, and should make use of encapsulation.</li>

 <li>You must use inheritance. If you don’t use inheritance you will lose a fair few marks.</li>

 <li>You can use polymorphism, if it’s appropriate.</li>

 <li>You need to overload operator++ as explained later. Other overloading, if you use it, should be sensible and appropriate.</li>

 <li>You need copy constructors associated with the evolution and devolution of the location.</li>

 <li>You can use your own data files for names or similar information.</li>

</ol>

<h1>1           An adventure in time</h1>

The year is 2525, and you have been appointed to supervise a team of chrononauts adventuring through time to collect information on the provenance and usage of various artefacts. The general overview is described below, but most of the details are up to you.

Your code should compile on Banshee according to instructions you provide in a Readme.txt file. Once your program is compiled into the executable AAT, it must run as follows:

./AAT n m

where <em>n </em>is the number of artefacts to be traced, and <em>m </em>is the number of jumps to be made for each artefact. The value of <em>n </em>should be in the range 1 to 5 inclusive. The value of <em>m </em>should be in the range 1 to 10 inclusive.

Your adventure takes place across the lifetime of a population centre, which in 2525 is a metropolis but at some distant historical point was a cluster of huts in a forest clearing near a source of clean water. You have an initial clue as to a period in the past when information on the artefact will be available. Each jump will take you to slightly before that date. You need to decide how to appropriately reduce the population centre in accordance with the size and technological era.

After each jump you step the population centre foward in time, year by year, using the overloaded ++ operator, until you find the information and an additional clue. It should typically take 5-10 years to find both of those. If no more jumps are allowed only the information needs to be gathered.

You should be reporting on all of the details of the population centre when you make a jump, so before and after. In the year by year stepping forward you can report on the technological and population levels each year, and otherwise just on events and the impact they have.

Report on the state of the chrononauts at the start and end of each jump period.

<h1>2           Simulation components</h1>

The simulation is from the perspective of the chrononauts. You need to give consistent and appropriate definitions for a class hierarchy associated with the various components of the adventure.

<h2>2.1         Artefacts, clues, and information</h2>

You should randomly generate an artefact. It should have a name and some sort of description. It should also have an estimated source time which should be relevant in determining where you jump. Across the search for an artefact it’s expected you will probably need to travel through at least two different technological eras.

The clues are effectively just a single number telling how much further to jump back for the next clue. The information is a percentage of the information about the artefact.

<h2>2.2         The population centre</h2>

There is only one population centre in the simulation but there are 5 different levels:

Hamlet, village, town, city, metropolis.

You need to decide the population ranges for each.

Each level should add relevant functionality on top of the previous one. It’s up to you to determine what that functionality is.

As an example, a town may have a medical centre. The name of that functionality may change when going to a larger population centre, so it might be called a hospital in a city, but there should also be something distinctive added as well.

In jumping you need to determine if a transition is needed, initially from metropolis to city. Transitions should be managed using copy constructors between adjacent levels. This means if your jump takes you from a metropolis to a town you go via a city.

Usually moving backwards in time results in a population decrease, and forwards a population increase, but the rate should vary depending on the population centre and the technology level. You should likely determine a base growth rate, possibly with saturation points, and have modifiers based on the population centre level, technological era, and events.

<h2>2.3         Technological eras</h2>

These are different time periods. These could be periods like the Stone Age, Middle Ages, or Information Age. It’s up to you to determine what they are called and the impact they have.

Usually moving backwards in time results in a technology decrease, and forwards a technology increase, but the rate should vary depending on the population centre and the technology level. You should likely determine a base growth rate, possibly with saturation points, and have modifiers based on the population centre level, technological era, and events.

<h2>2.4         Events</h2>

These occur within the year by year step with the chrononauts in the population centre. There could be development level and technology level change rates as a result of chrononaut influence, although they are supposed to limit this.

The following describe the events that could occur. The details are up to you, and there may not be an event every year.

<ol>

 <li>Finding artefact information. Assume there is only one lot of information that can be found in ajump site.</li>

 <li>Finding a jump clue. Assume only one jump clue can be found in a jump site.</li>

 <li>Very small chance of discovering the artefact you have, ”back” in 2525, is actually a fake. End ofthis search.</li>

 <li>Illness … Plague: Decrease population significantly. Could lose a chrononaut.</li>

 <li>Skirmish … War: Increase technology, decrease population. Could lose a chrononaut.</li>

 <li>Technological breakthrough: Increase in technology.</li>

 <li>Social revolution: Some sort of Decrease or Increase in the population, depending on the nature ofthe revolution.</li>

 <li>Interactions between chrononauts and locals: These could be positive or negative, and could changepopulation, technology, … . It’s up to you to determine the details.</li>

 <li>Chrononaut specific event: There should be some specific event relating to the chrononauts that youmake up.</li>

</ol>

To jump you have to obtain both the information and clue. The chances of these appearing should increase year by year, so that both should be found within 10 years.

<h2>2.5         The chrononauts</h2>

Each chrononaut should have a name, actual age, and travel age. The actual age doesn’t change. The travel age is the accumulated years spent in the population centre.

Provide characteristics for the travellers below to support their impact on the events. Each should have an ability level which influences how well they can perfom their task. The types of chrononauts are as follows:

<ul>

 <li><strong>Jump engineer</strong>: If you lose the jump engineer you are stuck. Jump engineers have special brain wiring that interferes with other functionality so they are otherwise pretty much useless, but they are also rare.</li>

 <li><strong>Doctor</strong>: Determines the likelihood of introducing or suffering from disease/death.</li>

 <li><strong>Historian</strong>: Determines the value of clues.</li>

 <li><strong>Security</strong>: Determines impact of interactions with locals.</li>

 <li><strong>Chrono-Pet</strong>: Should have some impact, to be determined by you.</li>

</ul>

You expect that abilities will slowly improve, as a function of technology level.