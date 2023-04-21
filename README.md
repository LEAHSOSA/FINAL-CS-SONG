# FINAL-CS-SONG
# Welcome to Sonic Pi
use_bpm 140
intro_effect="/Users/marthahernandez/Desktop/Pixies - Where Is My Mind (Official Lyric Video).wav"
vacations3_effect="/Users/marthahernandez/Desktop/VACATIONS 3- Young.wav"
vacations4_effect="/Users/marthahernandez/Desktop/VACATIONS 4- Young.wav"
vacations5_effect="/Users/marthahernandez/Desktop/VACATIONS 5- Young.wav"

vacations2_effect="/Users/marthahernandez/Desktop/VACATIONS 2 - Young.wav"
vacations1_effect="/Users/marthahernandez/Desktop/VACATIONS  1- Young.wav"
snip_effect="/Users/marthahernandez/Desktop/gril screm.wav"


tired_sleep =[1, 1,1,1,1,1,1,1,1,1,1,1,1,0.5,0.5,1,1,1,1,1,1]
tired_notes =[:c5,:e5,:c5,:e5,:c5,:e5,:c5,:e5,:b4,:e5,:b4,:e5,:c5,:c5,:b4,:c5,:e5,:c5,:e5,:c5,:e5]
x=0
y=0
s=1
index=0
y=index
x=index
define :function1 do |a,b,c|
  play:a
  sleep 2
  play:b
  play:c
  sleep 2
end
define:function_above do|d,e,f,g|
  play :d
  play :e
  play :f
  play :g
  sleep 1
end
transiton_effect="/Users/marthahernandez/Desktop/vacations.wav"

3.times do
  sample:ambi_piano,amp:s
  sleep 1
  s=s+0.5
end

sample intro_effect
sleep 1

sample snip_effect, amp: 5
sleep 20
live_loop:snap do
  5.times do
    sleep 3
    sample:drum_splash_hard,amp: 0.2
    sleep 1
  end
  stop
end

live_loop:tired do
  use_synth:piano
  21.times do
    play tired_notes[x]
    sleep tired_sleep [y]
    x=x+1
    y=y+1
  end
  stop
end
live_loop:extra_tired do
  use_synth:piano
  1.times do
    sleep 4
    sleep 4
    play:c3
    sleep 2
    play:c4
    play:g3
    sleep 2
    
    function1:a2,:a3,:e3
    
    play:e2
    play:e3
    sleep 2
    play:bs3
    play:gs3
    sleep 2
    
    play:f3
    play:f2
    sleep 2
    play:c4
    play:a3
    sleep 2
    
    function1:c3,:c4,:g3
    
  end
  stop
end

sleep 1
sample:vinyl_rewind

sleep 15
sample transiton_effect

sleep 25
sample vacations1_effect
use_bpm 72
notes =[:g4,:b4,:fs5,:e5,:fs5,:a4,:fs5,:g5]
index = 0
sleep 0.5
use_synth :sine

live_loop :top do
  8.times do
    play notes[index]
    sleep 0.5
    index=index+1
  end
  stop
  index=0
end


live_loop:this_better_work do
  3.times do
    play:g4
    sleep 0.5
    play:b4
    sleep 0.5
    play:fs5
    sleep 0.5
    play:e5
    sleep 0.5
    play:fs5
    sleep 0.5
    play:c5
    sleep 0.5
    play:fs5
    sleep 0.5
    play:g5
    sleep 0.5
  end
  stop
  play:b4
  sleep 0.5
  play:d5
  sleep 0.5
  play:a6
  sleep 0.5
  play:d5
  sleep 0.5
  play:a6
  
end
#stop after 4 times

live_loop :bottom do
  4.times do
    use_synth_defaults amp: 0.7
    function_above:e3,:d3,:b3,:g3
    
    function_above:e3,:d3,:b3,:g3
    
    play :e3
    play :c3
    play :a3
    sleep 1
    play :e3
    play :c3
    play :a3
    sleep 1
  end
  stop
end
sleep 20
sample vacations2_effect,amp:2

sleep 5
sample vacations3_effect,amp:3

sleep 7
sample vacations4_effect,amp:2

sleep 3
sample vacations5_effect,amp:1
