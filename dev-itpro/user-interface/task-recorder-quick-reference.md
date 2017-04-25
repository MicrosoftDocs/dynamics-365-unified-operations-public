---
# required metadata

title: Task Recorder quick reference
description: This article provides a quick reference sheet that explains what each button in the Task recorder menus does.
author: RobinARH
manager: AnnBe
ms.date: 04/04/2017
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: annbe
ms.search.scope: AX 7.0.0, Operations
# ms.tgt_pltfrm: 
ms.custom: 31141
ms.assetid: 8536e688-33f1-4f0c-a402-b1de2d253fbc
ms.search.region: global
# ms.search.industry: 
ms.author: shshabazz
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Task Recorder quick reference

[!include[banner](../includes/banner.md)]


This article provides a quick reference sheet that explains what each button in the Task recorder menus does.

Main menu
---------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><a href="./media/trquick01.png"><img src="./media/trquick01.png" alt="TRQuick01" class="alignnone size-full wp-image-290291" width="206" height="199" /></a></td>
<td><h3 id="create-recording">Create recording</h3>
Choose this option to begin creating a new recording.
<h3 id="play-recording-as-guide">Play recording as guide</h3>
Choose this option to see what your recording looks like when viewed as a Help topic or played as a Task guide.
<h3 id="change-recording-text">Change recording text</h3>
Choose this option if you need to change the recording’s name, description, or the text that is displayed in the steps.
<h3 id="update-recording-steps">Update recording steps</h3>
Choose this option if you need to add or remove steps. You can also use this mode to automatically play a recording</td>
</tr>
</tbody>
</table>

## Open and save options
<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td> <a href="./media/trquick02.png"><img src="./media/trquick02.png" alt="TRQuick02" class="alignnone size-full wp-image-290301" width="157" height="120" /></a><a href="./media/trquick03.png"><img src="./media/trquick03.png" alt="TRQuick03" class="alignnone size-full wp-image-290311" width="197" height="136" /></a></td>
<td><h3 id="opensave-fromto-this-pc">Open/Save from/to this PC</h3>
These options allow you to open a recording that is saved on your computer, or save a recording to your computer.
<h3 id="opensave-fromto-lcs">Open/Save from/to LCS</h3>
This option allows you to open a recording that has been saved to an LCS library, or save a recording to an LCS library.
<h3 id="open-from-recents">Open from recents</h3>
This option allows you to pick from a list of Task recordings that you have recently created.
<h3 id="export-as-work-document">Export as Work document</h3>
This option allows you to download a Word document that contains the list of steps in the recording.</td>
</tr>
</tbody>
</table>

## Playback controls
<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><a href="./media/trquick04.png"><img src="./media/trquick04.png" alt="TRQuick04" class="alignnone size-full wp-image-290321" width="177" height="116" /></a><a href="./media/trquick05.png"><img src="./media/trquick05.png" alt="TRQuick05" class="alignnone size-full wp-image-290331" width="208" height="120" /></a></td>
<td><h3 id="play-next-pending-step">Play next pending step</h3>
This option will cause Task recorder to execute and record the next pending step, which is indicated by the arrow in the Steps list.
<h3 id="play-to-selected-step">Play to selected step</h3>
This option will cause Task recorder to begin playing and recording pending steps, beginning at the next pending step and pausing after playing the step that was selected in the list when this option was clicked.
<h3 id="play-all-pending-steps">Play all pending steps</h3>
This option will cause Task recorder to play and record all remaining pending steps, until there are no remaining pending steps.
<h3 id="pause">Pause</h3>
This option only appears while playback is in progress. This option allows you to pause playback manually.</td>
</tr>
</tbody>
</table>

## Step actions
<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><a href="./media/trquick06.png"><img src="./media/trquick06.png" alt="TRQuick06" class="alignnone size-full wp-image-290341" width="225" height="98" /></a><a href="./media/trquick07.png"><img src="./media/trquick07.png" alt="TRQuick07" class="alignnone size-full wp-image-290351" width="223" height="99" /></a></td>
<td><h3 id="start-sub-taskend-sub-task">Start sub-task/End sub-task</h3>
These options allow you to add special steps to the recording. These special steps are task steps, and you can use them to indicate when a sub-task begins and when it ends. These options are disabled while playback is in progress.
<h3 id="delete-steprestore-step">Delete step/Restore step</h3>
These options allow you to remove steps from the recording. If you delete a pending step, it will be skipped during playback, and it will not be recorded. If you delete a recorded step, then it will be flagged for removal and it will not be included in the recording when you save the recording. You can only restore steps that have been successfully recorded. You cannot delete a task while it is in progress.</td>
</tr>
</tbody>
</table>

## Steps list
<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><a href="./media/trquick08.png"><img src="./media/trquick08.png" alt="TRQuick08" class="alignnone wp-image-290361 size-full" width="288" height="509" /></a></td>
<td><h3 id="step-counter">Step counter</h3>
<a href="./media/trquick09.png"><img src="./media/trquick09.png" alt="TRQuick09" class="alignnone size-full wp-image-290371" width="229" height="45" /></a>This keeps track of how many steps have been recorded. This includes steps played by using the Playback controls, as well as steps recorded by actions that you take in the client.
<h3 id="pending-steps">Pending steps</h3>
<a href="./media/trquick10.png"><img src="./media/trquick10.png" alt="TRQuick10" class="alignnone size-full wp-image-290381" width="223" height="67" /></a>This symbol represents a step that is pending and has not been recorded yet. Pending steps can be played using the Playback controls. When a pending step is played successfully, it is recorded and the symbol will update appropriately. <em>Pending steps are not included in the recording when you save the recording.</em> You must first play the pending steps so that they are recorded. If the steps are played and recorded successfully, then they will be included when you save the recording.
<h3 id="next-pending-step">Next pending step</h3>
<a href="./media/trquick11.png"><img src="./media/trquick11.png" alt="TRQuick11" class="alignnone size-full wp-image-290391" width="263" height="64" /></a>This symbol represents the next pending step. If you start playback, this is the first step that will be played.
<h3 id="queued-pending-steps">Queued pending steps</h3>
<a href="./media/trquick12.png"><img src="./media/trquick12.png" alt="TRQuick12" class="alignnone size-full wp-image-290401" width="250" height="57" /></a>This symbol represents pending steps that are queued for playback. This symbol is updated either when playback pauses, or when the queued pending step is played.
<h3 id="recorded-action-steps">Recorded action steps</h3>
<a href="./media/trquick13.png"><img src="./media/trquick13.png" alt="TRQuick13" class="alignnone size-full wp-image-290411" width="232" height="66" /></a>This symbol represents steps that were recorded successfully, either from being played back, or manually recorded by you.
<h3 id="recorded-info-steps">Recorded info steps</h3>
<a href="./media/recordedinfosteps.png"><img src="./media/recordedinfosteps.png" alt="RecordedInfoSteps" class="alignnone size-full wp-image-290491" width="208" height="70" /></a>This symbol represents an info step that was played and recorded. Info steps do not result in any action being executed on the application.
<h3 id="recorded-beginend-sub-task-steps">Recorded Begin/End sub-task steps</h3>
<a href="./media/trquick15.png"><img src="./media/trquick15.png" alt="TRQuick15" class="alignnone size-full wp-image-290431" width="226" height="66" /></a><a href="./media/trquick16.png"><img src="./media/trquick16.png" alt="TRQuick16" class="alignnone size-full wp-image-290441" width="230" height="64" /></a>These symbols indicate the beginning and ending of sub-tasks. Sub-task steps do not result in any action being executed on the application.
<h3 id="deleted-recorded-steps">Deleted recorded steps</h3>
<a href="./media/deletedrecordedsteps.png"><img src="./media/deletedrecordedsteps.png" alt="DeletedRecordedSteps" class="alignnone size-full wp-image-290501" width="233" height="69" /></a>This symbol represents a successfully recorded step that you have marked for deletion. Recorded steps that are marked for deletion will not be included when you save the recording. If a step has been successfully recorded when you decide to delete it, then you have the option to restore the deleted step before you save the recording.
<h3 id="deleted-pending-steps">Deleted pending steps</h3>
<a href="./media/trquick18.png"><img src="./media/trquick18.png" alt="TRQuick18" class="alignnone size-full wp-image-290461" width="218" height="63" /></a>If you delete a pending step, it will retain its pending symbol until it is played. When it is played, it will be skipped. You can restore a pending step as long as it has not been played and skipped.
<h3 id="skipped-steps">Skipped steps</h3>
<a href="./media/trquick19.png"><img src="./media/trquick19.png" alt="TRQuick19" class="alignnone size-full wp-image-290471" width="220" height="67" /></a>This symbol represents a step that was deleted while it was pending, and was skipped during playback. Skipped steps are not played and are not recorded. Because skipped steps are not recorded, they are not included when you save the recording. You cannot restore a skipped step.
<h3 id="error-steps">Error steps</h3>
<a href="./media/trquick20.png"><img src="./media/trquick20.png" alt="TRQuick20" class="alignnone size-full wp-image-290481" width="191" height="66" /></a>This symbol represents a step that was attempted by the playback system, but was not successful in being played. Error steps are not recorded, and are not included when you save the recording. You cannot restore an error step. Playback will automatically pause when an Error step is encountered. This gives you the opportunity to record replacement steps before continuing playback. An error step may occur for the following reasons:
<ul>
<li>The step could not play because the form or lookup needed by the step was not open.</li>
<li>The step could not play because the button or field needed by the step was disabled, not visible, or not present on the form.</li>
<li>The step could not play because the name of the form or name of the control has changed.</li>
<li>The step could not play because of a framework change to the control.</li>
</ul></td>
</tr>
</tbody>
</table>




