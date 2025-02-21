const audioContext = new (window.AudioContext || window.webkitAudioContext)();

const playNote = (frequency, startTime, duration) => {
   const oscillator = audioContext.createOscillator();
   const gainNode = audioContext.createGain();
   
   oscillator.type = 'square';
   oscillator.frequency.value = frequency;
   gainNode.gain.setValueAtTime(0.7, startTime);
   gainNode.gain.exponentialRampToValueAtTime(0.01, startTime + duration - 0.05);
   
   oscillator.connect(gainNode);
   gainNode.connect(audioContext.destination);
   
   oscillator.start(startTime);
   oscillator.stop(startTime + duration);
};

const frequencies = {
   'c4': 261.63,  // Low C
   'c5': 523.25,  // High C
   'd4': 293.66,
   'e4': 329.63,
   'f4': 349.23,
   'g4': 392.00,
   'a4': 440.00
};

const notes = [
   // First bar
   { freq: frequencies.g4, duration: 0.5 },    // G (quarter)
   { freq: frequencies.c4, duration: 0.5 },    // low C (quarter)
   { freq: 0, duration: 0.25 },                // rest (eighth)
   { freq: frequencies.c5, duration: 0.5 },    // high C (quarter)
   { freq: frequencies.a4, duration: 0.25 },    // A (quarter)

   // Second bar
   { freq: frequencies.g4, duration: 0.5 },    // G
   { freq: frequencies.c4, duration: 0.5 },    // low C
   { freq: 0, duration: 0.25 },                // rest
   { freq: frequencies.g4, duration: 0.5 },    // G (quarter)
   { freq: frequencies.f4, duration: 0.25 },   // F (eighth)

   // Third bar
   { freq: frequencies.e4, duration: 0.25 },   // E (eighth)
   { freq: frequencies.e4, duration: 0.25 },   // E (eighth)
   { freq: frequencies.f4, duration: 0.25 },   // F (eighth)
   { freq: frequencies.g4, duration: 0.25 },   // G (eighth)
   { freq: frequencies.c4, duration: 0.5 },    // C (quarter)
   { freq: frequencies.d4, duration: 0.5 },    // D (quarter)

   // Fourth bar
   { freq: frequencies.e4, duration: 1.0 }     // E (half)
];

const startTime = audioContext.currentTime;
let currentTime = startTime;

notes.forEach(note => {
   if (note.freq > 0) {
       playNote(note.freq, currentTime, note.duration);
   }
   currentTime += note.duration;
});
