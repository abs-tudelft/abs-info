# Typical MSc thesis outline

## Important remarks

- All chapter/section header, contents of tables/figures should have sentence capitalization (only first word of a sentence is capital).

- When referring to a specific figure, table, etc. by number, capitalize that word (Figure 1, Table 3, Page 5)

- If there is a Section 1.1, then there must be Section 1.2. A list of one item is not a list!

- Export all plots and diagrams as vectorized PDF. This ensures high quality figures with small file size. If you must use bit mapped pictures (e.g. png, jpg), limit resolution to 300ppi.

## 1. Introduction

1.1. Context (what is the project, where is it being carried out, how will this research have impact on the world)

1.2. Challenges (what is the general problem and what are the possible challenges to solving it)

1.3. Problem statement and research questions

1.4. Thesis outline

## 2. Background
    
Based on detailed analysis of the problem, discuss the various concepts related to the project that need more in-depth knowledge to understand the solution.

## 3. Alternative solutions
    
Start this chapter with a figure of a tree to classify the alternative solutions into classes
    
<p align="center">
  <img src="https://github.com/abs-tudelft/abs-info/blob/main/src/students/alternative_solutions.PNG" width="356" title="Alternative solutions">
</p>
    
3.1. Solution class 1 (discuss the solutions in this class)

3.2. Solution class 2 (discuss the solutions in this class)

3.3. Solution comparison (create table to compare the solutions qualitatively (using ++ and --) or quantitatively (using numbers) to choose the appropriate solution to implement)


## 4. Implementation

Here you implement the most appropriate solution chosen in Section 3.3.
    
4.1. Architectural details
    
4.2. Implementation of components

4.3. ..

## 5. Measurement results

5.1. Experimental setup (specs of systems you ran the experiments on, software stack used, datasets used if any, etc. The reader should be able to reproduce the results. Upload your code to a git repo and put a link to it in the text).

5.2. Multiple sections with results and discussion. Make sure to include an elaborate set of measurements to quantify e.g., the performance, bandwidth, accuracy, area, power, efficiency, etc. Perform these measurements not as a single point, but do measurements for a range of a number of design implementation parameters e.g., range of buffer sizes, range of input sizes, range of accuracy targets, scalability on multiple nodes, etc. The captions of the results figures should identify the experiment parameters different from other figures. Use markers, patterns and texture (not only color) to differentiate between multiple curves or bars in a figure. Don’t refer to colors in the text (10% of people are color blind)!

## 6. Conclusions and recommendations

6.1. Conclusions (re-state each research question from the introduction and discuss how you answered it in the thesis. The conclusions should not be new material, rather all conclusions should have been discussed in the thesis already in more detailed form)

6.2. Recommendations
