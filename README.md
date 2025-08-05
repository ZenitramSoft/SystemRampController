🔍 Overview
SystemRampController is a Lua script User Component designed for use within Q-SYS Designer. It manages:
Visual indicators
Loading meters
Color synchronization
for a system's Start and End sequences.
This component provides a dynamic and visually engaging way to represent system transitions, using ramping logic, color buckets, and shared meters. It is especially useful for creating intuitive feedback in user interfaces (UCIs) for AV systems.

🔧 Component Overview
Control Name	Description
SystemStart / SystemEnd	Buttons to initiate system start or end sequences
StartColor, EndColor, SharedColor	Dropdowns to select color themes
StartColorBucket, EndColorBucket, SharedColorBucket	Store selected color values and names
knbLoadingPercent, knbLoadingPercentReverse	Meters showing loading progress
knbSystemBothMeter	Shared meter for both directions
indPercent, indPercentNormal, indPercentReverse	Text indicators for loading percentages
indSystemStatus	Displays system status messages
indDebugWindow	Shows debug messages
btnBarColorChange	Toggle to sync shared meter color with Start/End color
btnCodeReset	Reloads the script component

▶️ Start Sequence (SystemStart)
Locks buttons to prevent double triggering
Updates color buckets and applies Start color
Resets meters to 0% (normal) and 100% (reverse)
Ramps up meters to simulate loading
Updates percent indicators to 100%
Displays status: "WARMING UP" → "ON"
Unlocks buttons after sequence completes

⏹ End Sequence (SystemEnd)
Locks buttons
Updates color buckets and applies End color
Resets meters to 0% (normal) and 100% (reverse)
Ramps down meters to simulate shutdown
Updates percent indicators to 0%
Displays status: "COOLING DOWN" → "OFF"
Unlocks buttons after sequence completes

🎨 Color Management
Color Buckets (StartColorBucket, EndColorBucket, SharedColorBucket) store the selected color and its string name.
Color Sync Toggle (btnBarColorChange):
When enabled, the shared meter (knbSystemBothMeter) color follows either the Start or End color depending on which button is active.
Color Choices:
A predefined list of named colors is available for selection, including shades of red, green, blue, purple, gray, and more.

🧪 Debugging & Feedback
Debug Window (indDebugWindow):
Displays real-time messages about system state and color changes.
System Status (indSystemStatus):
Shows user-facing status like "Press Start Or End", "WARMING UP", "ON", etc.

🛠 Initialization
On script load:
All meters and indicators are reset
Color buckets are hidden
Default values are applied
A welcome message is shown in the debug window

🧩 Functions Summary
funcInit():	Initializes all controls and indicators
funcUpdateLegends():	Syncs color choices and buckets
funcRampToFullStart() / funcRampToFullEnd():	Animates loading meters
funcSetLoadingBarToZero():	Resets loading meters to 0%
funcSetPercentToFull() / funcSetPercentToZero():	Sets shared meter to 100% or 0%
funcCheckSharedColor():	Determines which color to apply to shared meter
funcDebugger(who, why):	Logs debug messages
funcSetStartColor() / funcSetEndColor() / funcSetSharedColor()	Applies selected color to relevant controls
funcLockButtons(bool):	Enables/disables Start and End buttons
funcSystemStatus(string):	Updates system status text

🔁 Event Handling
Start/End Buttons trigger their respective sequences
Color Dropdowns update buckets and apply colors
Color Sync Toggle activates shared meter color logic
Script Reset Button reloads the script component
