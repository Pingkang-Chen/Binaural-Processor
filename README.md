Demo Video: Using this plugin for digital piano playing under 6Dof binaurall with headphone
https://youtu.be/wJ0qniDd1JE?si=1RoFfilRrDVx_Z7S

Plugin's UI:
<img width="950" alt="Screenshot 2025-05-09 at 21 10 13" src="https://github.com/user-attachments/assets/dfa86dde-24c7-499a-badd-3a0532bed101" />

Dynamic virtual acoustic environment(VAE) System Design: Direct sound is modeled by convolving the signal with the HRTF corresponding to the relative position (r, θ, ϕ) between the virtual source and the listener. In dynamic playback, the listener's head orientation is tracked in real time, and the HRTF lookup and convolution are updated accordingly. Early reflections are simulated using a simplified image-source method. The first- and second-order reflections are treated as independent virtual sources. Given the room geometry and positions of the listener and source, the spatial coordinates of each image source are computed. Each reflection undergoes delay (Delayi) and attenuation (αi) to simulate wall absorption and distance-dependent energy decay. These reflections are then spatialized using corresponding HRTFs (HL,i, HR,i) and the outputs are summed for both ears. During dynamic playback, the image source positions are continuously recalculated based on real-time head-tracking data, ensuring accurate spatialization of reflections. Late reverberation is synthesized using a Schroeder network consisting of four parallel comb filters and two serial all-pass filters. To avoid coloration, the delay lengths in the comb filters are set to irregular, non-integer values. The reverberation tail beyond 80 ms is decorrelated for the left and right ears before being added to the binaural output, ensuring spatial realism. Unlike the direct sound and early reflections, the late reverberation is modeled as a diffuse sound field that lacks directional properties, depending only on the room's acoustic parameters rather than source or listener orientation.
<img width="787" alt="Screenshot 2025-04-26 at 21 48 05" src="https://github.com/user-attachments/assets/e924b2af-ac31-46ce-a361-48958fbaa3da" />

Distance-based HRTF selection and processing flowchart:



<img width="577" alt="Screenshot 2025-04-18 at 16 02 48" src="https://github.com/user-attachments/assets/442d470c-9e48-4bbd-a362-bc134442bba4" />



1: You need to download the SOFA file used in this plugin through this link, and put it on your desktop before running this plugin:
https://sofacoustics.org/data/database/scut/SCUT_NF_subject0006_measured.sofa

2: Dependencies: JUCE, libmysofa

3: Build instructions: 

mkdir build

cd build

cmake ..

cmake --build .
