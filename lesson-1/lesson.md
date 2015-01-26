# Lesson 1: Getting started with Sonic Pi on a Raspberry Pi

The Raspberry Pi is a tiny computer, less than the size of a pack of cards, which can transform the way we perceive and approach computation. In this lesson, we will introduce the basic components of the Raspberry Pi and how they relate to a traditional computer. We will discuss the generic nature of computation and how the same computer can be programmed to simultaneously do many different things, from word processing to music synthesis. Finally, we will introduce the most basic principle of programming: a program as a sequence of instructions.

## Learning Objectives

- Know that there are many different types of computing devices.
- Understand how a computer uses a sequence of statements to do something, and that this sequence is called a program.
- Be able to give the Raspberry Pi some instructions to make some music.

## Learning Outcomes

### All students are able to:

- Know how to plug the components of a Raspberry Pi together.
- Act out some basic statements, and understand that a sequence of statements is a program.
- Write a simple program.

### Most students are able to:

- Create their own programs for others to act out, and have an idea of what might happen when it is acted out.

### Some students are able to:

- Invent their own statements.
- Start to explore the limitation of a program containing only statements and control flow.
- Understand the consequences of their program before they run it, and therefore design a musical program that's interesting to them.

## Lesson Summary

- An introduction to the basic physical parts of a Raspberry Pi
- A demonstration that the Raspberry Pi can behave like a traditional computer
- A group exercise to act out a simple program
- Starting the Sonic Pi application
- The first music program

## Starter

Have a demonstration Raspberry Pi already connected and the Sonic Pi software running. Hold up a Raspberry Pi board and ask the students what they think it is. Explain that it's actually a computer and that in the coming lessons we're going to do something special with it. Instead of running apps and games other people have created for us, we're going to learn to write our own software to make music.

Start the demo code below, play it for a moment or two and explain that in a few weeks the students will be able to make computers do this for themselves. Emphasise that they'll be free to do what they want with it and have a lot of fun in the process; programming is about getting the computer to do exactly what you want it to do. It's not important for the students to see the application or any code at this stage, just for them to hear the sounds coming from the computer.

```ruby
use_debug false

loop :low do |idx|
  #  idx = 0
  synth :zawa, wave: 1, invert_wave: 1, phase: 0.25, release: 5, note: :e1, cutoff: (range 60, 120, 10)[idx]
  sleep 4
  idx += 1
end

live_loop :lands, auto_cue: false do |idx|
  use_synth :dsaw
  use_random_seed 66679
  with_fx :reverb, room: 1  do
    16.times do
      ns = (scale :e2, :minor_pentatonic, num_octaves: 3)
      play ns.choose, detune: 12, release: 0.1, amp: 2, amp: rand + 0.5, cutoff: rrand(70, 120)
      sleep 0.125
    end
  end
end

live_loop :bikes do |idx|
  sleep 0.25
  sample :guit_em9, rate: -1
  sleep 7.75
end

live_loop :time, auto_cue: false do |idx|
  sample :bd_haus, amp: 2.5
  sleep 0.5
end

```

## Main Development

1. Start with all the parts of the Raspberry Pi on a table: keyboard, mouse, speaker, memory card, power supply, monitor, monitor cable and the Raspberry Pi itself. Ask the class to name and describe each component as you connect it to the Raspberry Pi in front of the class. Finally, plug in the power and watch it boot up. An alternative demonstration would be to leave out the memory card and attempt to boot the Pi, which will fail. You can then describe the memory card as something that contains instructions to tell the Raspberry Pi how to start. The Raspberry Pis should all be booted and sitting on the login prompt waiting for authentication.

1. Split the class into groups again and give each group a deck of the [computer program cards](files/Lesson-1-computer-program-cards.pdf). Ask each group to take out the statement cards and the control card from the deck. Then ask each group to form a line and to give each member of the group a statement card after shuffling them. The person at the start of the line should be given the control card. Explain that the person holding the control card should carry out the instructions on the statement card, and then pass the control card to the next person in the line like a relay baton. When the control card has reached the end of the line, they should stop. This should be repeated for a number of random orderings, after which the groups could be invited to create their own orderings. A helpful analogy might be cooking, where collections of statements are recipes and the control flow is which stage of the recipe you're at.

1. Start the Sonic Pi software. First, invite the students to log into their Raspberry Pi and start the graphical environment. It might help to display instructions on how to achieve this on a projector for all to see.

1. Explain to them that they can use the same statements on the cards in the computer program: `play` and `sleep`. Invite them to spend the remaining time writing their own programs and listening to the results.

## Plenary

Groups should be invited to choose card orderings for other groups to act out. Following this, a discussion should be held about how this relates to a computer. A computer works by executing statements one after another in a specific order. A given order of statements is called a **program**. Each program executes with a given **control flow**; this describes which statement we are executing and what the next statement will be.

## Homework

Students should be asked to invent statements of their own which they could act out with their family using the [Programming Statement Worksheet](files/Lesson-1-Statement-Worksheet.pdf).
