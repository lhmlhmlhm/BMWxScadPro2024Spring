<h1 style="margin-bottom:10px;color:#fff;border: none; ">Tech Team Guide - BMW x ScadPro Spring 2024 </h1>

---
<br/>
<br/>

# `/**** XR ****/`
<!-- Unity - UnityEngine.XR -->
# UnityEngine.XR (Package)
<!-- Struct -->
## Struct (Type)
<!-- Hand -->
### `'Hand'` &nbsp;&nbsp;[📖](https://docs.unity3d.com/ScriptReference/XR.Hand.html)
> A tracked hand on the device at an _**XRNode**_ in the XR input subsystem.
The Hand type represents a body element hierarchy corresponding to a human hand. It is comprised of Bone type elements.
#### Public Methods
**👉 Hand.TryGetFingerBones()** &nbsp;&nbsp;[📖](https://docs.unity3d.com/ScriptReference/XR.Hand.TryGetFingerBones.html)
|Description|Returns|
|-|-|
|Gets a list of the finger bones for a finger on this hand.|bool true if hand can be queried for this finger; otherwise false.|
```c#
public bool TryGetFingerBones(XR.HandFinger finger, List<Bone> bonesOut);
```
<br>

**👉 Hand.TryGetRootBone()** &nbsp;&nbsp;[📖](https://docs.unity3d.com/ScriptReference/XR.Hand.TryGetRootBone.html)
|Description|Returns|
|-|-|
|Gets the root bone for this hand.|bool true if hand can be queried for the root bone; otherwise false.|
```c#
public bool TryGetRootBone(out XR.Bone boneOut);
```
---
<!-- Enum -->
## Enum (Type)
<!-- XRNode -->
### `'XRNode'` &nbsp;&nbsp;[📖](https://docs.unity3d.com/ScriptReference/XR.XRNode.html)
> Enumeration of XR nodes which can be updated by XR input or sent haptic data.<br>📝 **Note:** The types GameController, TrackingReference, and HardwareTracker are considered non-singleton nodes, as there can be many of each available. As a result, _**InputTracking.GetLocalPosition**_, and _**InputTracking.GetLocalRotation**_ will not work with those values. Please use _**InputTracking.GetNodeStates**_ instead. Note: Only XR nodes with valid haptic devices as endpoints can be sent haptic data.
#### Properties
|||
|-|-|
|LeftEye|Node representing the left eye.|
|RightEye|Node representing the right eye.|
|CenterEye|Node representing a point between the left and right eyes.|
|Head|Node representing the user's head.|
|LeftHand|Node representing the left hand.|
|RightHand|Node representing the right hand.|
|GameController|Represents a tracked game Controller not associated with a specific hand.|
|TrackingReference|Represents a stationary physical device that can be used as a point of reference in the tracked area.|
|HardwareTracker|Represents a physical device that provides tracking data for objects to which it is attached.|

---
<br>

# `/**** Input ****/`
<!-- Unity - UnityEngine -->
# UnityEngine (Package)
<!-- UnityEngine.InputSystem -->
## Namespace: UnityEngine.InputSystem &nbsp;&nbsp; [📖](https://docs.unity3d.com/Packages/com.unity.inputsystem@1.7/api/UnityEngine.InputSystem.html)
<!-- Class -->
## Class (Type)
<!-- InputActionReference -->
### `'InputActionReference'` &nbsp;&nbsp;[📖](https://docs.unity3d.com/Packages/com.unity.inputsystem@1.7/api/UnityEngine.InputSystem.InputActionReference.html)
> References a specific InputAction in an InputActionMap stored inside an InputActionAsset.
```c#
public class InputActionReference : ScriptableObject
```
#### Remarks
The difference to a plain reference directly to an _**InputAction**_ object is that an InputActionReference can be serialized without causing the referenced _**InputAction**_ to be serialized as well. The reference will remain intact even if the action or the map that contains the action is renamed.

References can be set up graphically in the editor by dropping individual actions from the project browser onto a reference field.
#### Demo
```c#
using UnityEngine;
using UnityEngine.InputSystem;

// Example script to demonstrate the usage of InputActionReference
public class InputActionReferenceExample : MonoBehaviour
{
    public InputActionReference inputActionReference;

    void OnEnable()
    {
        // Convert the InputActionReference to InputAction and enable it
        var inputAction = inputActionReference.action;
        inputAction?.Enable();
    }

    void OnDisable()
    {
        // Disable the InputAction when the script is disabled
        inputActionReference.action?.Disable();
    }
}

/* Properties Detailed Comments */

/*
action
- Declaration: public InputAction action { get; }
- Property Value: InputAction, the action that the reference resolves to. Null if the action cannot be found.
- Remarks: Actions are resolved on demand based on their internally stored IDs.
*/

/*
asset
- Declaration: public InputActionAsset asset { get; }
- Property Value: InputActionAsset, the asset that the referenced action is part of. Null if the reference is not initialized or if the asset has been deleted.
*/

/* Methods Detailed Comments */

/*
Create(InputAction)
- Declaration: public static InputActionReference Create(InputAction action)
- Parameters: InputAction action - An input action to be referenced.
- Returns: InputActionReference, a new InputActionReference object that references the given action.
- Remarks: The input action must be contained in an InputActionMap that is itself contained in an InputActionAsset.
*/

/*
Set(InputAction)
- Declaration: public void Set(InputAction action)
- Parameters: InputAction action - The input action to set the reference to.
- Exceptions: InvalidOperationException if the action is not contained in an InputActionMap that is itself contained in an InputActionAsset.
*/

/*
Set(InputActionAsset, String, String)
- Declaration: public void Set(InputActionAsset asset, string mapName, string actionName)
- Parameters: InputActionAsset asset, String mapName, String actionName - Specifies the asset, map name, and action name to set the reference.
- Exceptions: ArgumentNullException if asset, mapName, or actionName is null or empty. ArgumentException if no matching action map or action could be found.
*/

/*
ToInputAction()
- Declaration: public InputAction ToInputAction()
- Returns: InputAction, the InputAction object this reference points to.
*/

/*
ToString()
- Declaration: public override string ToString()
- Returns: String, a string representation of the reference useful for debugging.
- Overrides: Object.ToString()
*/

/* Operators Detailed Comments */

/*
Implicit Conversion (InputActionReference to InputAction)
- Declaration: public static implicit operator InputAction(InputActionReference reference)
- Parameters: InputActionReference reference - The InputActionReference object to convert.
- Returns: InputAction, the action pointed to by the reference. Can be null.
- Usage: Allows InputActionReference to be used directly where InputAction is expected, enhancing code readability.
*/

/* Example Usage:
You can assign an InputActionReference in the Unity Editor by dragging and dropping an InputAction from an InputActionAsset. In scripts, use the `inputActionReference.action` to access the actual InputAction and perform operations like Enable or Disable.
*/
```
---

<!-- Enum -->
## Enum (Type)

<!-- TouchPhase -->
### `'TouchPhase'` &nbsp;&nbsp;[📖](https://docs.unity3d.com/Packages/com.unity.inputsystem@1.7/api/UnityEngine.InputSystem.TouchPhase.html)
> Indicates where in its lifecycle a given touch is.
```c#
public enum TouchPhase
```
#### Demo
```c#
// import
using TouchPhase = UnityEngine.InputSystem.TouchPhase;
// use
var primaryTouchPhase = activeTouches[0].phase;
if (primaryTouchPhase == TouchPhase.Began)
{
  ...
}
```
#### Field
| Name | Description | Value |
| -------- |:--------:| --------:|
|None|No activity has been registered on the touch yet.|0|
|Began|A touch has just begun.|1|
|Moved|An ongoing touch has changed position.|2|
|Ended|An ongoing touch has just ended.|3|
|Canceled|An ongoing touch has been cancelled.|4|
|Stationary|An ongoing touch has not been moved (not received any input) in a frame.|5|
#### Extension Methods
> InputExtensions.IsEndedOrCanceled() &nbsp;&nbsp;[📖](https://docs.unity3d.com/Packages/com.unity.inputsystem@1.7/api/UnityEngine.InputSystem.InputExtensions.html#UnityEngine_InputSystem_InputExtensions_IsEndedOrCanceled_UnityEngine_InputSystem_TouchPhase_) <br>
InputExtensions.IsActive() &nbsp;&nbsp;[📖](https://docs.unity3d.com/Packages/com.unity.inputsystem@1.7/api/UnityEngine.InputSystem.InputExtensions.html#UnityEngine_InputSystem_InputExtensions_IsActive_UnityEngine_InputSystem_TouchPhase_)

---
<br>

<!-- UnityEngine.InputSystem.EnhancedTouch -->
## Namespace: UnityEngine.InputSystem.EnhancedTouch &nbsp;&nbsp; [📖](https://docs.unity3d.com/Packages/com.unity.inputsystem@1.7/api/UnityEngine.InputSystem.EnhancedTouch.html)

<!-- Class -->
## Class (Type)

<!-- EnhancedTouchSupport -->
### `'EnhancedTouchSupport'` &nbsp;&nbsp;[📖](https://docs.unity3d.com/Packages/com.unity.inputsystem@1.7/api/UnityEngine.InputSystem.EnhancedTouch.EnhancedTouchSupport.html)
> API to control enhanced touch facilities like Touch that are not enabled by default.
```c#
public static class EnhancedTouchSupport
```
#### Remarks
- **Automatic Finger Tracking**: Simplifies tracking by automatically managing each finger's interaction on the touchscreen.
- **Touch History Recording**: Keeps a record of all touch interactions, useful for analyzing touch patterns and sequences.
- **Polling-Based**: Designed for direct querying of touch states, typically within the MonoBehaviour.Update method.
- **Not Compatible with InputActions**: Cannot be used with InputActions simultaneously but both systems can be employed side-by-side in a project.

#### Demo
```c#
using UnityEngine;
using UnityEngine.InputSystem.EnhancedTouch;

// Example usage of EnhancedTouchSupport
public class EnhancedTouchExample : MonoBehaviour
{
    protected void OnEnable()
    {
        // Enable enhanced touch support when the GameObject is enabled
        EnhancedTouchSupport.Enable();
    }

    protected void OnDisable()
    {
        // Disable enhanced touch support when the GameObject is disabled
        EnhancedTouchSupport.Disable();
    }

    protected void Update()
    {
        // Log active touches
        var activeTouches = Touch.activeTouches;
        for (var i = 0; i < activeTouches.Count; ++i)
        {
            Debug.Log("Active touch: " + activeTouches[i]);
        }
    }
}

/* Class EnhancedTouchSupport Detailed Comments */

/* Properties */

/*
enabled
- Declaration: public static bool enabled { get; }
- Property Value: Boolean. True if EnhancedTouch support has been enabled.
- Meaning: Indicates whether the enhanced touch support is currently active.
*/

/* Methods */

/*
Disable()
- Declaration: public static void Disable()
- Remarks: Disables enhanced touch support. To completely disable it, you must call Disable() for each previous call to Enable().
- Usage: Typically called when cleaning up or when no longer needing enhanced touch functionalities.
*/

/*
Enable()
- Declaration: public static void Enable()
- Remarks: Enables the enhanced touch functionalities provided by Touch and Finger. Since these APIs add additional processing, they are disabled by default. Enable() and Disable() calls balance each other, meaning repeated calls to Enable() require an equal number of calls to Disable() to turn the system off.
- Usage: Call this method to start using enhanced touch features like automatic finger tracking and touch history recording. Necessary for games or applications relying on touch input.
*/

/* Note: The EnhancedTouchSupport class offers a straightforward way to enable or disable enhanced touch functionalities in Unity. By using the Enable() and Disable() methods, developers can control when these features are active, ensuring efficient use of resources and optimal performance according to the application's needs. Remember, enhanced touch support is designed for polling in methods like Update and cannot be used simultaneously with InputActions, though they can be utilized side-by-side for different input handling purposes. */

```
---
<!-- Finger -->
### `'Finger'` &nbsp;&nbsp;[📖](https://docs.unity3d.com/Packages/com.unity.inputsystem@1.7/api/UnityEngine.InputSystem.EnhancedTouch.Finger.html)
> A high-level representation of a touch which automatically keeps track of a touch over time.
```c#
public class Finger
```
#### Remarks
- Touchscreen Support: Each touchscreen has a capacity for a limited number of concurrent touches, determined by the hardware's capability.

- Finger vs. Touch:
  - A "Finger" is a virtual representation, not directly tied to a physical finger on a user's hand.
  - It stays consistent and valid throughout the lifespan of its corresponding Touchscreen.
  - The term "Finger" is used to track the sequence of touches on the screen. For instance, the first touch detected is associated with the first Finger instance, regardless of which actual physical finger is used.
- Dynamic Representation:
  - The same "Finger" instance may represent touches from different physical fingers at different times. It's not locked to a specific physical finger (like an index or ring finger) but rather represents the Nth touch on the screen.

#### Demo
```c#
using UnityEngine;
using UnityEngine.InputSystem;
using UnityEngine.InputSystem.EnhancedTouch;

// Example usage of Finger class
public class FingerInputHandler : MonoBehaviour
{
    private void Update()
    {
        // Iterate through all fingers on the first touchscreen
        foreach (var finger in Touchscreen.current.fingers)
        {
            // Check if the finger is currently active
            if (finger.isActive)
            {
                Debug.Log($"Finger {finger.index} is touching the screen at position {finger.screenPosition}");
            }
        }
    }
}

/* Class Finger Detailed Comments */

/*
currentTouch
- Declaration: public Touch currentTouch { get; }
- Property Value: Touch, the currently ongoing touch or default if no touch is in progress.
- Meaning: Provides access to the current touch associated with this finger, if any.
*/

/*
index
- Declaration: public int index { get; }
- Property Value: Int32, index of the finger on screen.
- Meaning: Represents the Nth touch on the screen, where N is the finger's index.
*/

/*
isActive
- Declaration: public bool isActive { get; }
- Property Value: Boolean, whether the finger is currently touching the screen.
- Meaning: Indicates if there is an ongoing touch for this finger.
*/

/*
lastTouch
- Declaration: public Touch lastTouch { get; }
- Property Value: Touch, the last touch registered or default if no touch has occurred.
- Remarks: Last touch transitions to a new touch as soon as a new one starts on this finger.
- Meaning: Access to the most recent touch associated with this finger, until a new touch begins.
*/

/*
screen
- Declaration: public Touchscreen screen { get; }
- Property Value: Touchscreen, the screen associated with this finger.
- Meaning: The touchscreen device this finger is associated with.
*/

/*
screenPosition
- Declaration: public Vector2 screenPosition { get; }
- Property Value: Vector2, current position on the screen or default if no ongoing touch.
- Meaning: Provides the current screen position of the active touch for this finger.
*/

/*
touchHistory
- Declaration: public TouchHistory touchHistory { get; }
- Property Value: TouchHistory, full touch history of the finger.
- Remarks: History size is limited by maxHistoryLengthPerFinger. Older entries get overwritten by newer ones when the limit is reached.
- Meaning: Access to the historical touch data for this finger, capped at a maximum length.
*/

/* Note: For each property, detailed comments include its declaration, property value or type, remarks where applicable, and a general meaning or usage indication. These comments aim to give a clear and comprehensive understanding of each property's role in managing touch inputs through finger instances in Unity's Enhanced Touch System. */

```
---
<br>

<!-- Struct -->
## Struct (Type)

<!-- TouchPhase -->
### `'Touch'` &nbsp;&nbsp;[📖](https://docs.unity3d.com/Packages/com.unity.inputsystem@1.7/api/UnityEngine.InputSystem.EnhancedTouch.Touch.html)
> A high-level representation of a touch which automatically keeps track of a touch over time.
```c#
public struct Touch : IEquatable<Touch>
```
#### Remarks
- Simplification of Touch Management:
  - Eliminates the need for manual tracking of touch identifiers (_**touchId**_) and touch phases (_**phase**_), facilitating easier differentiation between individual touches.
- Enhanced Touch Tracking:
  - Provides protection against losing brief touches that might occur within the same input update cycle. This is an improvement over traditional methods where a new touch in the same update could overwrite a short-lived touch.
- Distinction Between Fingers and Touches:
  - **Touches**: Represents a single contact state change event on the touchscreen, categorized into actions like beginning (Began), moving (Moved), or ending (Ended or Canceled) touches.
  - **Fingers**: Refers consistently to the Nth contact on the screen, not tied to physical fingers but to the sequence of touch points.
- Data Structure and Storage:
  - A _**Touch**_ instance is a struct linking to the actual data, which is stored in unmanaged memory. This struct merely references the data, ensuring efficient memory usage and access.

#### Demo
```c#
using UnityEngine;
using UnityEngine.InputSystem;
using UnityEngine.InputSystem.EnhancedTouch;
using System;

// Example class to demonstrate usage of Touch properties, methods, and events.
public class TouchInputHandler : MonoBehaviour
{
    void Awake()
    {
        // Enable EnhancedTouch at the start of the script
        EnhancedTouchSupport.Enable();
    }

    void Update()
    {
        // Iterate over active touches
        foreach (var touch in Touch.activeTouches)
        {
            if (touch.began)
                Debug.Log($"Touch began at {touch.screenPosition}");
            else if (touch.ended)
                Debug.Log($"Touch ended at {touch.screenPosition}");
        }
    }

    private void OnEnable()
    {
        // Subscribe to touch events
        Touch.onFingerDown += OnFingerDown;
        Touch.onFingerMove += OnFingerMove;
        Touch.onFingerUp += OnFingerUp;
    }

    private void OnDisable()
    {
        // Unsubscribe from touch events
        Touch.onFingerDown -= OnFingerDown;
        Touch.onFingerMove -= OnFingerMove;
        Touch.onFingerUp -= OnFingerUp;
    }

    // Example method for finger down event
    private void OnFingerDown(Finger finger)
    {
        Debug.Log($"Finger down at {finger.screenPosition}");
    }

    // Example method for finger move event
    private void OnFingerMove(Finger finger)
    {
        Debug.Log($"Finger moved to {finger.screenPosition}");
    }

    // Example method for finger up event
    private void OnFingerUp(Finger finger)
    {
        Debug.Log($"Finger up from {finger.screenPosition}");
    }
}

/* Properties Detailed Comments */

/*
activeFingers
- Declaration: public static readonly ReadOnlyArray<Finger> activeFingers { get; }
- Property Value: ReadOnlyArray<Finger>, a set of currently active fingers.
- Exceptions: InvalidOperationException if EnhancedTouch has not been enabled.
- Meaning: Represents the touch contacts that currently have an active touch.
*/

/*
activeTouches
- Declaration: public static readonly ReadOnlyArray<Touch> activeTouches { get; }
- Property Value: ReadOnlyArray<Touch>, all touches that are either ongoing or have ended in the current frame.
- Remarks: Ensures touches that begin and end or move within a single frame are accurately tracked.
- Exceptions: InvalidOperationException if EnhancedTouch has not been enabled.
*/

// For the sake of brevity, I will summarize a few more properties and then move on to methods and events.

/*
began
- Declaration: public readonly bool began { get; }
- Property Value: Boolean, indicates if the touch has begun this frame.
- Meaning: True if the touch phase is Began, false otherwise.
*/

/*
delta
- Declaration: public readonly Vector2 delta { get; }
- Property Value: Vector2, screen-space motion delta of the touch.
- Remarks: Delta behavior may differ from other controls, detailed in documentation.
*/

/* Methods Detailed Comments */

/*
Equals(Object)
- Declaration: public override bool Equals(object obj)
- Parameters: Object obj - The object to compare with the current object.
- Returns: Boolean - true if the specified object is equal to the current object; otherwise, false.
- Overrides: ValueType.Equals(Object)
*/

/*
Equals(Touch)
- Declaration: public bool Equals(Touch other)
- Parameters: Touch other - The Touch instance to compare with the current object.
- Returns: Boolean - true if the specified Touch instance is equal to the current object; otherwise, false.
- Implements: IEquatable<T>.Equals(T)
*/

/* Events Detailed Comments */

/*
onFingerDown
- Event Type: Action<Finger>
- Declaration: public static event Action<Finger> onFingerDown
- Exceptions: InvalidOperationException if EnhancedTouch has not been enabled.
- Meaning: Invoked when a finger touches the Touchscreen.
*/

/*
onFingerMove
- Event Type: Action<Finger>
- Declaration: public static event Action<Finger> onFingerMove
- Exceptions: InvalidOperationException if EnhancedTouch has not been enabled.
- Meaning: Invoked when a finger that is in contact with a Touchscreen moves on the screen.
*/

/*
onFingerUp
- Event Type: Action<Finger>
- Declaration: public static event Action<Finger> onFingerUp
- Exceptions: InvalidOperationException if EnhancedTouch has not been enabled.
- Meaning: Invoked when a finger lifts off from a Touchscreen.
*/

/* Note: For properties, methods, and events not explicitly detailed here, follow the same comment structure to fill in the details based on the documentation provided. This template aims to guide how to encapsulate and describe functionalities provided by the Touch struct in a way that's informative and directly useful for development purposes. */
```
---
<!-- TouchHistory -->
### `'TouchHistory'` &nbsp;&nbsp;[📖](https://docs.unity3d.com/Packages/com.unity.inputsystem@1.7/api/UnityEngine.InputSystem.EnhancedTouch.TouchHistory.html)
> A fixed-size buffer of Touch records used to trace the history of touches.
```c#
public struct TouchHistory : IReadOnlyList<Touch>, IReadOnlyCollection<Touch>, IEnumerable<Touch>, IEnumerable
```
#### Remarks
> This struct provides access to a recorded list of touches.
#### Demo
```c#
using UnityEngine;
using UnityEngine.InputSystem.EnhancedTouch;
using System.Collections.Generic;

// Example usage of TouchHistory
public class TouchHistoryExample : MonoBehaviour
{
    void Update()
    {
        // Accessing touch history for the first finger if it is active
        if (Touchscreen.current.fingers[0].isActive)
        {
            TouchHistory history = Touchscreen.current.fingers[0].touchHistory;

            // Iterate through touch history from newest to oldest
            foreach (var touch in history)
            {
                Debug.Log($"Touch at {touch.screenPosition} with phase {touch.phase}");
            }
        }
    }
}

/* Struct TouchHistory Detailed Comments */

/* Properties */

/*
Count
- Declaration: public readonly int Count { get; }
- Property Value: Int32, the number of history records available.
- Implements: IReadOnlyCollection<T>.Count
- Meaning: Indicates the total number of touch records stored in the history.
*/

/*
Item[Int32]
- Declaration: public readonly Touch this[int index] { get; }
- Parameters: Int32 index - Index of the history record (0 == newest, Count - 1 == oldest).
- Property Value: Touch, returns a touch history record by index.
- Implements: IReadOnlyList<T>.Item[Int32]
- Exceptions: ArgumentOutOfRangeException if index is less than 0 or >= Count.
- Meaning: Allows accessing individual touch records by index, facilitating analysis of touch patterns over time.
*/

/* Methods */

/*
GetEnumerator()
- Declaration: public IEnumerator<Touch> GetEnumerator()
- Returns: IEnumerator<Touch>, enumerator over the touches in the history.
- Implements: IEnumerable<T>.GetEnumerator()
- Usage: Enables enumeration over touch records, from newest to oldest, which is useful for iterating through the touch history in a foreach loop or similar construct.
*/

/* Explicit Interface Implementations */

/*
IEnumerable.GetEnumerator()
- Declaration: IEnumerator IEnumerable.GetEnumerator()
- Returns: IEnumerator, supports simple iteration over the collection.
- Implements: IEnumerable.GetEnumerator()
- Meaning: Provides a non-generic iterator for the touch records, allowing the touch history to be used in contexts that expect an enumerable but do not require type specifics.
*/

/* Note: TouchHistory struct is a powerful tool for tracking and analyzing touch inputs over time, making it particularly useful in applications that require detailed touch analysis, such as gesture recognition or drawing applications. It provides both a count of stored touch records and indexed access to these records, along with enumeration capabilities for easy iteration. */

```
---
<br>

<!-- Unity - PolySpatial -->
# PolySpatial (Package)
<!-- Spatial Pointer Device Data -->
## Spatial Pointer Device Data &nbsp;&nbsp;[📖](https://docs.unity3d.com/Packages/com.unity.polyspatial.visionos@1.0/manual/PolySpatialInput.html#spatial-pointer-device-data)
>The SpatialPointerDevice in visionOS integrates with SwiftUI's SpatialEventCollection, facilitating content interaction through gesture-based inputs.
#### Remarks
- **Primary Interaction Mechanism**: Users interact with content by looking at an object and performing gestures, like a pinch with the index finger and thumb.
- **Input Variants**: 
  - **Indirect Pinch**: Registered by the aforementioned looking and pinching gesture.
  - **Direct Touch (Poke)**: Physical contact with the object.
  - **Direct Pinch**: Physical pinching gesture on the object.
- **Concurrent Inputs**: Supports up to two simultaneous inputs.
- **Collider Requirement**: Objects must have a collider to receive input.
- **Input Pose Information**: The _'inputDevicePosition'_ and _'inputDeviceRotation'_ properties convey the pose of the interacting device, typically based on the user's pinch gesture.
- **Interaction Ray Default**: Initially, the interaction ray aligns with the user's eye gaze, directing the focus of interaction.
```c#
using UnityEngine;

public class SpatialPointerHandler : MonoBehaviour
{
    private SpatialPointerDevice spatialPointerDevice;

    void Awake()
    {
        // Initialize your SpatialPointerDevice here
        // This is a placeholder since SpatialPointerDevice is not a standard Unity class
        spatialPointerDevice = new SpatialPointerDevice();
    }

    void Update()
    {
        if (spatialPointerDevice == null) return;

        // Check the interaction phase
        if (spatialPointerDevice.phase == SpatialPointerPhase.Started)
        {
            // Interaction started
            Debug.Log($"Interaction started at {spatialPointerDevice.startInteractionPosition} on object {spatialPointerDevice.targetObject.name}");
        }
        else if (spatialPointerDevice.phase == SpatialPointerPhase.Moved)
        {
            // Interaction moved
            Debug.Log($"Interaction moved. Delta: {spatialPointerDevice.deltaInteractionPosition}");
        }
        else if (spatialPointerDevice.phase == SpatialPointerPhase.Ended)
        {
            // Interaction ended
            Debug.Log($"Interaction ended at {spatialPointerDevice.interactionPosition}");
        }

        // Additional properties can be used as needed, for example:
        // - Accessing the interaction's world position
        // - Getting the input device's position and rotation
        // - Identifying the kind of interaction
        // - Checking for modifier keys
    }

    // Example method to handle spatial interaction, demonstrating usage of various properties
    void HandleSpatialInteraction()
    {
        Vector3 interactionPos = spatialPointerDevice.interactionPosition;
        Vector3 deltaPos = spatialPointerDevice.deltaInteractionPosition;
        Vector3 startPos = spatialPointerDevice.startInteractionPosition;
        // Use these vectors as needed for your application logic

        Quaternion inputDeviceRotation = spatialPointerDevice.inputDeviceRotation;
        // Use the rotation as needed for your application logic

        if (spatialPointerDevice.targetObject != null)
        {
            // Direct reference to the target object
            Debug.Log($"Interacting with {spatialPointerDevice.targetObject.name}");
        }
    }
}
```
---
<br>

# `/**** Display ****/`
<!-- Unity - TMPro -->
# TMPro (Package)
<!-- UnityEngine.InputSystem.EnhancedTouch -->
## Namespace: TMPro &nbsp;&nbsp; [📖](https://docs.unity3d.com/Packages/com.unity.textmeshpro@1.3/api/TMPro.TMP_Text.html)
<!-- Class -->
## Class (Type)
<!-- TouchHistory -->
### `'TMP_Text'` &nbsp;&nbsp;[📖](https://docs.unity3d.com/Packages/com.unity.textmeshpro@1.3/api/TMPro.TMP_Text.html)
>Base class which contains common properties and functions shared between the TextMeshPro and TextMeshProUGUI component.
```c#
public abstract class TMP_Text : MaskableGraphic
```
#### Inheritance
1. Object
   - TMP_Text
2. TextMeshPro
3. TextMeshProUGUI
#### demo
```c#
using UnityEngine;
using TMPro; // Assuming TMP (TextMeshPro) namespace

[RequireComponent(typeof(TextMeshProUGUI))] // Or TextMeshPro for 3D texts
public class TextController : MonoBehaviour
{
    private TextMeshProUGUI textComponent;

    void Start()
    {
        textComponent = GetComponent<TextMeshProUGUI>();

        // Example usage of setting text
        textComponent.text = "Hello, World!";

        // Adjusting font size and enabling auto-sizing
        textComponent.enableAutoSizing = true;
        textComponent.fontSizeMin = 12;
        textComponent.fontSizeMax = 48;

        // Applying color and a simple color gradient
        textComponent.color = new Color(1, 1, 1); // White
        textComponent.colorGradientPreset = CreateGradientPreset();
        textComponent.enableVertexGradient = true;
    }

    TMP_ColorGradient CreateGradientPreset()
    {
        // Define a simple gradient from red to blue
        return new TMP_ColorGradient(Color.red, Color.blue, Color.red, Color.blue);
    }

    void Update()
    {
        // Example dynamic text update
        textComponent.text = $"Time: {Time.time:F2}";
    }
}
```
#### Notes on Implementation
- **Fields like** _'m_actionStack'_, _'m_fontAsset'_, etc., suggest internal workings of the TextMeshPro system, handling font data, rendering details, and layout calculations. Direct interaction with these fields is typically abstracted away from the user, with interaction primarily through public properties and methods.
- **Properties like** _'fontSize'_, _'color'_, **and** _'text'_ are publicly accessible and are used to adjust the text appearance. They're straightforward to use, as shown in the example.
- **Methods such as** _'SetText()'_ or _'UpdateVertexData()'_ indicate functionality to change the text content or update the mesh data. In practice, setting the _'.text'_ property or similar properties often internally calls these methods to reflect changes.
- **Gradient, Padding, and Material Adjustments** are managed via properties (_'colorGradientPreset'_, _'extraPadding'_, _'fontMaterial'_), allowing for fine-tuning of text appearance beyond simple color or font size adjustments.

---
<br>