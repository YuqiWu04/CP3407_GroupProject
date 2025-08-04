Iteration 2 Retrospective
1. Finished and Incomplete User Stories
In Iteration 2, our team successfully completed all user stories and associated tasks set out for this cycle. The primary focus was on user stories 3 (“Identify Common Errors”) and 4 (“Learning Experience”), both of which were not completed in the previous iteration. For this iteration, we set out to finish tasks that were directly tied to these stories, breaking them down into smaller, actionable components.

All of the following user stories and tasks were fully completed by the end of the iteration:

Identify Common Errors (User Story 3)

3.1: Match the colors detected to components of internet concepts

3.2: Use cloud or local memory to store the matching rules and corresponding concepts

3.3: Create edit function for teacher's end

3.4: Create user interaction interface for the function

Learning Experience (User Story 4)

4.1: Get segmented polygons and fill them onto a blank mask

4.2: Extract the largest contour and approximate it into a quadrilateral

4.3: Perform perspective transformation on the image

4.4: Split the image into grids and get ROIs

4.5: Detection and matching of colors within the grid

4.6: Draw the results on the original canvas

All items listed above were both started and completed within the defined iteration window, and the outcomes have been validated against the acceptance criteria for each story. There are no outstanding or incomplete user stories/tasks from this sprint, reflecting excellent team commitment and focus.

2. Completion Relative to Estimated Duration
Our total estimated workload for Iteration 2 was 14 days of effort, distributed across four developers. The actual burn down closely tracked our estimates:

4 weeks left: 14 days of estimated work

2 weeks left: 12 days

1 week left: 6 days

0 weeks left: 0 days

All planned tasks were completed on schedule, with an actual velocity of 0.62 (slightly below the assumed 0.7 from Iteration 1). The minor deviation in velocity is explainable primarily by technical challenges encountered (see below), but importantly, all work was finished before the deadline. This reflects solid estimation practice, especially as the iteration included technically demanding integration of computer vision and frontend visualization components.

3. Obstacles Encountered by the Team
Despite the successful delivery, our team encountered several notable obstacles:

Model Segmentation Output Issues
Initially, the segmentation model (accessed via the Roboflow serverless endpoint) did not return valid or usable results for several input cases. Sometimes, the segmentation mask was missing or the detected polygon did not match the expected LEGO board region, making further processing impossible.

Analysis Failures on Segmented Results
Once segmentation output was obtained, there were difficulties in reliably extracting the correct board contour and approximating it to a quadrilateral, which is a prerequisite for perspective transformation. Noisy masks or poorly approximated polygons caused the pipeline to fail early, returning no useful grid for subsequent color detection.

Visualization of Analyzed Results
Even when analysis succeeded, it proved difficult to accurately visualize the results on the original camera frame. Mapping between the rectified (warped) grid and the original camera coordinates required precise handling of perspective matrices and correct overlay logic. In some cases, the color annotations were misplaced or overlapped incorrectly, reducing the interpretability of the results.

4. How These Obstacles Were Cleared
The solutions to these obstacles are now well-documented and reflected in the current project source code:

Reliable Segmentation and Robust Error Handling
The segmentation module (LegoSegmenter) was improved to robustly handle cases where the segmentation API returned null or empty predictions, preventing pipeline crashes and allowing user feedback for failed casessegmentationsegmentService.

Contour Extraction and Perspective Correction
The analysis logic (LegoBoardAnalyzer) was enhanced to:

Smooth segmentation masks and filter out noise with morphological operations and stricter color matching thresholds.

Always search for the largest valid contour and only proceed if a quadrilateral can be reliably approximatedlegoBoardAnalyzer.

Use perspective transformations (OpenCV’s getPerspectiveTransform and warpPerspective) to standardize the board region, making downstream grid-splitting consistent and accurate.

Precise Visualization and Overlay Mapping
The visualization module (VisionApp) was updated to map detected cell quadrilaterals back to the original image using the inverse perspective matrix. Convex hull algorithms were used to group and annotate areas of the same color/component, ensuring that overlays and text labels (e.g., protocol components) were always displayed in the correct positions on the user’s screenvision.

Comprehensive Debug Logging
Throughout the codebase, debug statements and error logs were inserted at each critical processing stage, significantly reducing debugging time and improving maintainability.

5. Potential Process Improvements for Future Iterations
Based on our experiences this iteration, the following process improvements are suggested for future cycles:

Earlier and Automated Integration Testing
Several integration bugs could have been caught earlier if there had been automated end-to-end tests running the full pipeline (from image capture to final overlay display) on a suite of representative input images. Instituting such tests would catch API contract changes or edge case failures before they impact multiple team members.

Incremental, Feature-Gated Releases
During this iteration, some features (e.g., color mapping and grid overlay) were blocked until segmentation and perspective transformation were finalized. Adopting a more modular, feature-gated approach—where downstream features are developed and tested using stubbed/mock data—would allow parallel progress even if one part of the pipeline is delayed.

Improved Communication and Standups
Daily short standups focused specifically on blockers could improve the speed at which obstacles are raised and cleared, preventing individual contributors from being stuck for extended periods.

User Feedback Loops
Introducing short user testing sessions mid-iteration would provide earlier feedback on the usability and accuracy of the visual overlays and analytics dashboards, leading to a more polished end product.

Enhanced Documentation
Clearer internal documentation, especially around the structure and contract of API responses, would help new contributors ramp up faster and reduce the risk of misunderstandings.

Conclusion:
Despite challenging technical obstacles, Iteration 2 was a full success: all user stories and tasks were completed within the planned duration, and the core pipeline—from camera capture through segmentation, board analysis, and visualization—has matured substantially. Lessons learned from this iteration will be leveraged to streamline future work and further improve both the team’s workflow and the final product’s quality.
