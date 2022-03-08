---
layout: default
title: Home
nav_order: 1
---

<button class="btn js-toggle-dark-mode">Dark mode</button>

<script>
const toggleDarkMode = document.querySelector('.js-toggle-dark-mode');

jtd.addEvent(toggleDarkMode, 'click', function(){
  if (jtd.getTheme() === 'dark') {
    jtd.setTheme('light');
    toggleDarkMode.textContent = 'Dark mode';
  } else {
    jtd.setTheme('dark');
    toggleDarkMode.textContent = 'Return to the light mode';
  }
});
</script>

# RM03: Spatial Analysis and Modelling

Welcome to 2021-2022 lent term module RM03 : Spatial Analysis and Modelling.  
Meterials of supervision could be found below.

## Course outline

| Lectures      | Topic                                                                                                                                                                                                                             | Lecturers                                    |
|---------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------|
| Lecture 1     | Introduction: Concepts, theory and practice in spatial analysis using GIS and data science                                                                                                                                        | (Elisabete A. Silva)                         |
| Lecture 2     | Data types of data, data collection and processing: from census to new live data harvesting in a digital age of big data                                                                                                          | (Elisabete A. Silva)                         |
| Lecture 3     | GIS and Data Processing: vector/raster/image data sets                                                                                                                                                                            | (Elisabete A. Silva)                         |
| Lecture 4     | Spatial metrics & analysis: static and dynamic environments                                                                                                                                                                       | (Elisabete A. Silva & H. Niu)             |
| **Supervision 1** | **Introduction of spatial analysis using Quantum GIS(QGIS)** [[Exercises]](supervision1-exercises.md) [[Assignment]](supervision1-assignment.md)<!--  [[Slides]](./RM03_supervision1_slides.pdf) [[Exercises]](supervision1-exercises.md)[[Assignment]](supervision1-assignment.md)[[Answer]](supervision1-answer.md) --> | (H. Niu, A. Seraphim)                         |
| Lecture 5     | Urban and Environmental Dynamic Modelling                                                                                                                                                                                         | (Elisabete A. Silva)                        |
| Lecture 6     | Dynamic simulation models SA, MCA, ABM, CA, GA and NN: development, calibration, validation                                                                                                                                       | (Elisabete Silva)                            |
| **Supervision 2** | **Netlogo - urban modelling** [[Exercises]](supervision2-exercises.md)[[Assignment]](supervision2-assignment.md)<!--  [[Slides]](./RM03_supervision2_slides.pdf)[[Exercises]](supervision2-exercises.md)[[Assignment]](supervision2-assignment.md)[[Answer]](supervision2-answer.md)-->                                  | (P. M. Scherer, A. Seraphim)                  |
| Lecture 7     | Hot topics in Spatial analysis and new technologies                                                                                                                                                                               | (H. Niu, Y. Chen, P. M. Scherer, A. Seraphim) |
| **Supervision 3** | **Linking Big Data(harvesting & mining) with QGIS**  [[Exercises]](supervision3-exercises.md) <!--[[Slides]](./RM03_supervision3_slides.pdf)[[Exercises]](supervision3-exercises.md) -->                                                                                       | (H. Niu, Y. Chen)                            |
| Lecture 8     | Data Science, Complexity Theory and Adaptive Planning                                                                                                                                                                             | (Elisabete A. Silva)                         |
| Revision Supervision        | TBC                                                                                                                                                                                                                               |
|


**Format** : Three in-person supervision sessions. Each session will be given in 50 mins to two groups (6-8 students in each group).

<!-- **Preparation &amp; Platform** : The supervision will be given via **Microsoft Teams**, a supported online collaboration tool for the University. Please download and test Microsoft Teams and **log in with your Cambridge Microsoft account** (not your personal account) before the first supervision. Before each supervision, supervisors will invite you to chat groups by your Cambridge email address (Please make sure you are using the right account). Check the following link for installation instruction and how to share your screen within group chat: [Setup Microsoft Teams](https://hn303.github.io/CamLandEc-RM03/setup_teams){:target="\_blank"}. -->

<!-- Related Links:

- [Microsoft Teams at Cambridge Hub](https://help.uis.cam.ac.uk/news/teams-launch){:target="\_blank"}
- [How to get Teams](https://universityofcambridgecloud.sharepoint.com/sites/MicrosoftTeamsHub/SitePages/How-to-get-Teams.aspx){:target="\_blank"}
- [How to log in to your University of Cambridge Microsoft account](https://help.uis.cam.ac.uk/service/accounts-passwords/microsoft-accounts/ees-login){:target="\_blank"} -->

**Booking supervision** : You will find supervision scheduler on Moodle with the assigned slots. Due the aviablibity of supervision room, supervisors would strictly stick to the enrolled lists on the scheduler. Please send us H.NIU if you need to change your slots.

**Supervision materials** : During each supervision, we will ask students to go through supervision exercises with provided instruction. The supervisor and demonstrator will be there if you have any difficulties during the practice. The material for the supervision exercise will be released in advance. You should follow the instruction to download the required software as preparation. Please note that you do NOT need to practice the supervision exercise before each supervision. After each supervision, we will release the supervision assignment via Moodle. Students should submit their assignments via Moodle by the deadline. Please note that there is no assignment for supervision 3 and revision supervision.

| Material      | _Supervision Exercises_ | _Supervision Assignment_ | Software       |
|---------------|-------------------------|--------------------------|----------------|
| Supervision 1 | Yes                     | Yes                      | QGIS           |
| Supervision 2 | Yes                     | Yes                      | Netlogo        |
| Supervision 3 | Yes                     | No                       | Google Account |
| Revision Supervision | No                      | No                |                |


**Computer &amp; Software** : All software engaged in this supervision, e.g.., QGIS, Python and Netlogo, are open-sourced and compatible on Linux, Windows and macOS. Students are expected to use their own laptops with software installed in advance.

### Contributors

This repo is created by [**Haifeng Niu**](https://haifengniu.com/en/){:target="\_blank"} and contributed by Heeseo Rain Kwon, Paul Scherer and Yiqiao Chen.

### License

<a rel="license" href="http://creativecommons.org/licenses/by-nc-sa/4.0/"><img alt="Creative Commons License" style="border-width:0" src="https://i.creativecommons.org/l/by-nc-sa/4.0/88x31.png" /></a><br />This work is licensed under a <a rel="license" href="http://creativecommons.org/licenses/by-nc-sa/4.0/">Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License</a>.
