# Exptime

#Cricket Game Simulation
import random
import matplotlib.pyplot as plt
#name = input('Welcome to Pycricket! And your name is..?')
#default name for now is Gucci (non-interactive)
name = "Gucci"

#game greeting
print ("Alright " + name + ", you have one over to play, maximize it!!!\n")


#function generating a random number and related outcome (7 possibilities) for each ball in the over (each pitch)
def cric():
    global x
    global b
    x  = random.randrange(2,8)
    if x != 5 and x != 7:
        print str(x) + "!"
    elif x == 5:
        print ("0!")
    elif x == 7:
        print ("W!")
    if x==1:
        print (name + " delicately guides the ball to third man for a single.")
    elif x==2:
        print (name + " slashes it to point past the fielder for a couple")
    elif x==3:
        print (name + " flicks it over long on with a majestic touch for three")
    elif x ==4:
        print (name + " produces an elegant straight drive as the bowler is a mere spectator")
    elif x ==5:
        print (name + " swings hard but is beaten by sheer pace. The ball rockets through to the keeper")
    elif x ==6:
        print (name + " charges the bowler and connects! The ball is launched over long-on") 
    elif x==7:
        print (name + " is comprehensively beaten by a viscious in-swinger. That's the end of your innings")
        b = 6
        
#while loop to cycle back into the function in order to simulate an over (6 pitches max in an over)
#two lists created for ball and runs to create a graph 
ball = []
runs = []
b = 1
total = 0
while b<7:
    cric()
    ball.append(b)
    if x != 7 and x != 5:
        total = (x) + total
        runs.append(x)
    else:
        total = total
        runs.append(0)
    b += 1

#concluding message based on results (runs scored)
print ("\nThat's the end of your over " + name + "!" + " You've scored " + str(total) + " runs.\n")
if total < 10:
    print "Better luck next time eh?"
elif 10 < total < 20:
    print "Thats decent homie"
elif total > 20:
    print "Rocking performance mate!"
#creating a customized graph based on performance using the lists created (ball and runs)    
plt.bar(ball,runs, color = 'g', linewidth = 3)
plt.title('Your Game Summary!')
plt.xlabel('Ball #')
plt.ylabel('Runs')
plt.style.use('dark_background')
plt.show()
