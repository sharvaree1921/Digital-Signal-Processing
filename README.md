# Digital-Signal-Processing
 Coursera -DSP1

## Introduction-
There has always been two models infront of us to study Digital Signal Processing.One in which we describe things in the form of functions and calculus and the other via sets of numerical measurement.DsP has its achievment in the latter approach.However,Sampling Theorem provides the bridge between them.

## What is Digital Signal Processing?
**Signal**-Signal is just the description of the evolution of physical phenomena.It is the means to convey the information of a particular event or phenomena.
**Processing**-Processing is comprised of Two parts-_analysis_ and _synthesis_.Analysis means understanding the information carried by the signal and Synthesis means creating a signal to contain given information.

We have many examples where occurence of some phenomena is described in terms of some functions.For example->RC circuit,projection in kinematics,etc.have their specific functions associated with it.Now consider a signal of say speech i.e.recorded by some recorder.Here,we can't represent that signal as some function of time or anything.We don't have set of rules that define it.The devices used in recording do tell us about what the signal is,but are unable to tell us how the signal is that only.So,this signal is just continuous set of values,also called as **analog signal**.So,we are moving from analog to digital type just to represent the signal as a series of numbers.And this paradigm shift is of two types **discrete time** and **discrete amplitude**.

Let's start with Discrete time concept.Adopt and model the reality where signals are described as sequences. 
Mathematically these are mappings from a set of integers to a set of values, V, which could be the set of real numbers.
Or, as in the case of fully digital signals a set of integers as well.The notation is very simple.We will indicate a discrete time signal as x of n where x is our signal and n is quote on quote time. We will see pretty soon that n does not have a physical dimension. It's just an ordinal number that orders the samples one after the other. 
But,are we losing some information in discrete time representation? The answer to this question was given by some scientists,suggesting that under very mild conditions,continuous time representations and discrete time representations are equivalent.Mathematically this result is called,**Sampling Theorem**.We can make the continuous representation using discrete representation and linear combination of copies of typical function called the **sinc shifted** and scaled by the values of discrete time sequence. The sinc function is symmetrical and oscillates from -infi to +infi.Check out this [here](https://www.coursera.org/learn/dsp1/lecture/ioZFl/1-1-1-what-is-digital-signal-processing).
Given a continuous signal.We record measurements at particular equal intervals and ditch off the remaining part.so,this would be our discrete signal pattern.To recover original continuous signal,we apply sync function to each sample location scaled by the amplitude.And then add this all calculated functions to get original continuous waveform.The conditions for doing this are stated in the statement of sampling theorem and the tool to do this is **Fourier Analysis**.The Fourier transform will give us a quantitative measure of how fast a signal moves. And once we know this speed, we will always be able to choose a sampling interval, namely a space between measurements when we convert a function to a sequence that will satisfy the hypothesis of the sampling theory. 

Now,Let's look at concept of Disrete Amplitude.Where each sample can take values now only amongst a predetermined set of possible levels.And the very important consequence of discretization is that independently on the number of levels, the set of levels is countable.So we can always map the level of the sample onto an integer. 
Now,if our data is just a set of integers,then its representation is completely abstract and completely general.And this has important consequences in three domains-**storage**,**processing** and **transmission**.
_Storage_ becomes very easy as any system that can store integers can also store signals now.
_Processing_ becomes completely independent on the nature of the signal because all we need is a processor which deals with integers.CPUs are excellent examples of suuch processors.
_Transmission_ can be made very much effective by reducing noise and inreasing the capacity of communication channel.

### Data Transmission-
Suppose we want to transmit our data from transmitter to the reciever via a communication channel,we are faced with a fundamental problem of noise.While transmitting the signal,first our signal will be attenuated(reduction of amplitude of signal) with introduction of some noise.So,our final output signal will be (original signal/G + noise).
But,at receiver side,we want the original signal as it is.So,we have to undo the attenuation and noise introduced.So basically,multiplying by G to undo attenuation,we get-(original signal + noise x G).The problem here,we see is that the noise is also increased.
Suppose,we want to transmit analog signal from America to India(a way long),we need the _repeaters_ to do so for retreiving the original signal.Repeaters perform attenuation and de-attenuation repeatedly,but in this process,our noise is being amplified again and again,which is a huge problem.In _N_ such sections our noise will be NxG implying loss of whole information that we want to transmit.
Now,consider the same case,just that we are transmiting Digital signal instead of analog.Digital signal is composed of samples whose values belong to some set of finite accountable values i.e. integers.Now,transmitting set of integers means that we uncode the integers in binary format and thus transmitting basically the sequence of 0's and 1's.Suppose we assign +5V as '1' and -5V as '0'.And we will have a signal which will also layout these two levels as digits are transmitted.What happens on the channel is the same as before.We will have an attenuation, we will have the addition of noise, and we will have an amplifier at each repeater then will try and undo the attenuation.But on top of it all we will have what's called a threshold operator then we'll try to reconstitute the original signal as best as possible. 
So,till addition of noise,it is same as before.Let's say that in the threshold operator,if the signal value is above zero, we just output 5 volts and vice versa.If it's below zero, we will output minus 5 volts.So the thresholding operator will reconstruct a signal like so. Hence,we can see that,the original signal is retreived,and not a noise corrupted copy.

## Discrete Time Signal-
Discrete time signal can be referred as a sequence of complex numbers.
1. One Dimension(for now)
2. Notation : x[n]
3. Two sided sequences-x:Z->C
4.n is _a-dimensional_ 'time'
5.Analysis-periodic movement
6.Synthesis-Stream of Generated Samples.

Various types of Discrete Time Signals-
1. **Delta Function**-
The function has the value '0' at all locations of n except at 0,its value is infinity.
2. **Unit Step Function**-
Its value is zero for all n<0 and is 1 for all values of n greater than 0.It acts like a switch.
3. **The exponential decay function**-
When n is less than zero,its value is 0 and when n is greater than 0 its value exponentially decays.
Example-Discharging of a Capacitor in RC circuit,Newton's law of cooling.
4. **The Sinusoid**-
Oscillatory signals are found everywhere.

There are four signal classes-
1. **Finite Length**
-Sequence Notation-x[n],n=0,1,2,...N-1
-Vector Notation-x[n]=[x0 x1 x2 ... x(N-1)]
-Practical Entities,good for numerical packages(ex-Numpy)

However,it's not possible to develop whole signal processing theory,only by using finite discrete set of values. 

2. **Infinite Length**
-Sequence Notation-x[n],n belongs to Z.
-Abstraction,good for theorems.
3. **Periodic**-
N-periodic sequence- x[n]=x[n+kN], n,k,N belongs to Z.
Same information as finite-length of length N.
'Natural' bridge between Finite and Infinite lengths.
4. **Finite support**
x[n]=x[n] if 0<=n<=N,x[n]=0 otherwise.
Same information as finite length of length N.
Another bridge between finite and infinite lengths.

We also have definition of **energy**.It is sum of all elements in the sequence of the square magnitudes of elements.Many sequences have infinite amount of energy,like unit step function.f you do the sum, you will see that E to the x goes to infinity. So to describe the energetic properties of the sequences, we use the concept of power. The power is the rate of production of energy for a sequence, and it is defined as the limit for capital N that goes to infinity of the local energy computed over a window of size 2N + 1 divided by the size of the window. 

### How your PC plays discrete time sounds?
Do check it out [here](https://www.coursera.org/learn/dsp1/lecture/ORbNE/1-1-3-a-how-your-pc-plays-discrete-time-sounds)

## The Karplus-Strong Algorithm-
First we will deal with some building blocks which are necessary to build any complex circuit in Digital Electronics.Some of them are as follows-
1-**Adder**-x[n]+y[n]
2-**Multiplier**-x[n] * p=px[n]
3-**Unit Delay**-x[n]->x[n-1]
4-**Arbitrary Delay**-x[n]->x[n-N]

**The two point moving Average**-
Simple average:m=(a+b)/2
Moving Average:Take a local Average:y[n]=(x[n]+x[n-1])/2

A must watch video-[Watch Now](https://www.coursera.org/learn/dsp1/lecture/NpNjI/1-1-3-b-the-karplus-strong-algorithm)

## Complex Exponentials-
To clear basics of Complex numbers waych [here](https://www.coursera.org/learn/dsp1/lecture/Z437t/1-1-4-complex-exponentials)
Especially watch the last part-must [watch](https://www.coursera.org/learn/dsp1/lecture/Z437t/1-1-4-complex-exponentials)
