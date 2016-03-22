# Prototype


1. User loads CT lung study from a DICOMWeb server in the OHIF Viewer
2. OHIF Viewer asks slicer to describe a study given a study UID via RESTful API call.  Note that in the future we will want to trigger this when receiving the DICOM so the study description can be calculated in advance avoiding any delays during study loading. [examine API](../restAPI/examine.md)
3. Slicer pulls metadata from DICOMWeb via WADO-RS Retrieve Metadata and DICOM Plugins to describe the study
4. Slicer returns the study description to OHIF Viewer (e.g. Volumetric views, segmentation tools available, etc) [examine API](../restAPI/examineJob.md)
5. OHIF Viewer updates viewports with indicators based on study description (e.g. Axial series can be viewed as MPR or VR, segmentation tools available, etc)
6. User scrolls through series/stack and clicks on a nodule
7. OHIF Viewer asks Slicer to perform segmentation with the necessary information via RESTful API call (seed point in patient coordinate system, images related to segmentation, etc) [segment API](../restAPI/segmentationJob.md)
8. OHIF Viewer monitors slicer’s status for the segmentation request (e.g. Polls a restful endpoint or listens for an event via websockets/ddp) [segment API](../restAPI/segmentationJob.md)
9. OHIF Viewer downloads segmentation results via RESTful API call (e.g. Segmentation returned as DICOM Segmentation Object, other JSON data from results of computation) [DICOMSEG API](../restAPI/DICOMSEG.md)
10. OHIF Viewer displays dicom segmentation object as overlay on slices user views along with other commutation results (e.g. Table showing dose absorbed by voxels in segmentation)

I propose that we initially skip a few steps to create a spike/demo/POC:

2. – Skip - OHIF Viewer to use a hard coded study description
3. – Skip – Preload study into Slicer’s cache
4. – Skip - OHIF Viewer to use a hard coded study description
5. – Hard code segmentation tool activation based on hard coded study description

After this is done, we will know more and can revisit the plan.
