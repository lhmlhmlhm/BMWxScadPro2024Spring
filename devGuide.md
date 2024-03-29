<h1 style="margin-bottom:10px;color:#fff;border: none; ">Tech Team Guide - BMW x ScadPro Spring 2024 </h1>

---
<br/>
<br/>


<!-- Unity - UnityEngine -->
# Unity - UnityEngine (Package)
<!-- UnityEngine.InputSystem -->
<h2 style="display:inline-block;color: #DF6060">Namespace: &lt;UnityEngine.InputSystem&gt;&nbsp;&nbsp;
    <a href="https://docs.unity3d.com/Packages/com.unity.inputsystem@1.7/api/UnityEngine.InputSystem.html">📖</a></h2>

<!-- Enum -->
<h2 style="display:inline;color:#6ADF60;">Enum</h2>

<!-- TouchPhase -->
### `TouchPhase` &nbsp;&nbsp;[📖](https://docs.unity3d.com/Packages/com.unity.inputsystem@1.7/api/UnityEngine.InputSystem.TouchPhase.html)
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

<br>

---
<h2 style="display:inline-block;color: #DF6060">Namespace: UnityEngine.InputSystem.EnhancedTouch&nbsp;&nbsp;
    <a href="https://docs.unity3d.com/Packages/com.unity.inputsystem@1.7/api/UnityEngine.InputSystem.EnhancedTouch.html">📖</a></h2>
<!-- Class -->
<h2 style="display:inline;color:#6ADF60;">Class</h2>

<!-- Finger -->
### `Finger` &nbsp;&nbsp;[📖](https://docs.unity3d.com/Packages/com.unity.inputsystem@1.7/api/UnityEngine.InputSystem.EnhancedTouch.Finger.html)
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
<br>

---
<br>
<!-- Struct -->
<h2 style="display:inline;color:#6ADF60;">Struct</h2>

<!-- TouchPhase -->
### `TouchPhase` &nbsp;&nbsp;[📖](https://docs.unity3d.com/Packages/com.unity.inputsystem@1.7/api/UnityEngine.InputSystem.EnhancedTouch.Touch.html)
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
<!-- Unity - PolySpatial -->
# Unity - PolySpatial (Package)


