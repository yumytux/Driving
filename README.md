# L-Plan

A lesson planner for driving instructors. After a lesson, you dictate your notes and can add a screenshot from TotalDrive. Claude then:

- summarises the lesson (what went well, what to work on)
- suggests changes to the pupil's skill levels on the 1–5 ADI scale, for you to accept or untick
- writes the next lesson plan: goals, a timed outline, route ideas, briefing points and faults to watch for

Each plan can be copied into TotalDrive.

The app is a single page, `lesson-planner/index.html`, published as a Claude artifact. It uses the artifact runtime for private storage (`db`, saved under the instructor's own account) and for Claude calls (`sample`, with images for screenshots), so there are no API keys or servers to look after.
