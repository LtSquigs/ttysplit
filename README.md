ttysplit
========

A simple node utility that you can use to split a ttyrec into a smaller part


Usage:
========

`node ttysplit.js target_file.ttyrec [start_frame] [end_frame]`

The program will split the given ttyrec starting at start_frame and ending at end_frame. The split file is output on stdout.

If start_frame and end_frame are not supplied, the program instead spits out the total number of frames in the recording.

I should also note, the split file does not always start at start frame, for complex applications that use ANSI escape characters to partially redraw the screen, starting at an arbitrary frame may result in strange visuals. As a result the program looks for the ANSI screen clearing sequence (At least the one used by nethack, for which this was designed) and will use the last frame before start_frame that has the clear sequence.

Examples:
========

`node ttysplit.js  2011-08-05.22-58-04.ttyrec 11277 > splitRecording.ttyrec`

splitRecording.ttyrec will contain a recording starting from 11277 till the end of the recording (or whichever closest frame before it has an ANSI clear sequence)

`node ttysplit.js  2011-08-05.22-58-04.ttyrec 1 500 > splitRecording.ttyrec`

This will split the recording from frame 1 to 500

`node ttysplit.js  2011-08-05.22-58-04.ttyrec `

This will output the total number of frames in the recording. For example `11283`
