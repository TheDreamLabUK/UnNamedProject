# Proposal: Augmented Reality on a Spinning Vinyl Record via Persistence of Vision

Imagine pointing your phone camera at a turntable where a custom-pressed vinyl record is spinning. It's playing your favourite album. On your phone screen, the record isn't just a black disc; the area near the edge, printed with those specific concentric rings, resolves into a clear, steady circular pattern despite the rotation – a subtle, almost technical-looking barcode shimmering slightly from the persistence of vision processing.

Suddenly, rising virtually from the record's surface, perhaps aligned with the label, is a dynamic piece of AR content. It could be:

A miniature 3D diorama of the band performing the current track.
Floating, interactive liner notes or lyrics that scroll in time with the music.
Abstract visualizations that pulse and react to the audio frequencies, seemingly emanating from the grooves.
The album cover art, standing upright in 3D, casting a virtual shadow on the vinyl.
As you move your phone around, closer or further away, the AR element remains perfectly locked to the record's surface. It spins with the vinyl, flawlessly maintaining its position and orientation because the camera is constantly reading that synthesized barcode pattern. Tilting the phone shows different angles of the AR object, reinforcing the illusion that it's physically present and interacting with the spinning record. It transforms passive listening into an interactive visual experience, directly linked to the physical media.

## Overview

This project proposes using a standard mobile phone camera and OpenCV to create an augmented reality (AR) experience overlaid onto a spinning vinyl record. The core technique relies on generating a **persistence of vision** effect from the spinning record's surface, which contains a specially designed pattern.

## Technique

1.  **The Target:** A standard 30cm vinyl record is modified to include a pattern of 8 concentric rings. These rings vary in width (e.g., between 2cm and 4cm) based on a chosen encoding scheme, acting as a circular barcode. The minimum feature size is ~2cm.
2.  **Image Capture:** A mobile phone camera captures the spinning record at a standard frame rate (e.g., 30fps).
3.  **Persistence of Vision Synthesis:** OpenCV processes the video feed, averaging groups of consecutive frames (e.g., 3-6 frames) to produce a lower frame rate output (5-10fps). This averaging creates a persistence of vision effect, making the rapidly moving ring pattern appear as stable, solid concentric circles.
4.  **Detection & Orientation:** OpenCV functions (like Hough Circle Transform and contour analysis) detect these synthesized concentric rings. The specific pattern (widths/spacing) of the rings is decoded to determine the record's precise **orientation relative to the camera**.
5.  **AR Rendering:** Using the calculated orientation, AR content (3D models, information overlays, visual effects) can be accurately rendered onto the record's surface as viewed through the phone's screen. The AR elements will appear anchored to the vinyl and rotate correctly with it.

## Technology Stack

* **Hardware:** Standard mid-range smartphone, modified vinyl record.
* **Software:** OpenCV library (Python or C++), AR rendering engine/library (like ARCore, ARKit, or a 3D engine with camera integration).

## Outcome

The system will allow stable and accurately oriented AR experiences directly tied to a physical spinning vinyl record, using the record itself as the tracking marker through the persistence of vision effect.
