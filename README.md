# Custom-reference-monitor
# Implement a Defensive Security System
This assignment will help you understand security mechanisms. You will be guided through the steps of creating a reference monitor using the security layer functionality in Repy V2. A reference monitor is an access control concept that refers to an abstract machine that mediates all access to objects by subjects. This can be used to allow, deny, or change the behavior of any set of calls. While not a perfect way of validating your reference monitor, it is useful to create test cases to see whether your security layer will work as expected (the test cases may be turned in as part of the next assignment).

This assignment is intended to reinforce concepts about access control and reference monitors in a hands-on manner.

# Overview
In this assignment, you will implement a defense monitor to oversee file operations in Repy. The monitor will enhance the default Repy behavior by adding an undo functionality for writes. This defense monitor will ensure that software follows certain rules and guidelines, preventing potential unauthorized actions.

The focus is on monitoring file write operations and allowing the last write to be reverted. This undo capability mimics common document editors that let you reverse your most recent edit.

You should write test applications to ensure your reference monitor behaves properly in different cases and to test attacks against your monitor.

# Specifications:
Your defense monitor should incorporate all the standard file operation methods, with an added method named undo.
A writeat operation will not immediately write its changes to the file. The changes will only be permanent after either of the following occur:
A subsequent valid writeat operation is executed.
The file is closed.
The undo operation will reverse the changes of the last valid writeat operation, making it as if it didn't happen. It's crucial to note that only the most recent operation can be undone. If there haven't been any writeat operations, the undo has no effect. If several writeat operations are consecutively executed, only the changes from the last valid writeat can be undone.
Aside from the ability to be undone and potentially delayed writes, all writeat operations should behave the same way as they do in the RepyV2 API.

# Three design paradigms are at work: accuracy, efficiency, and security.

Accuracy: The defense monitor should precisely and consistently manage file operations. Only specific operations, such as writeat, should have their behavior modified. All situations that are not described above must match that of the underlying API.

Efficiency: The security layer should use a minimum number of resources, so performance is not compromised. For example, you may not call readat() everytime writeat() is called. It is permissable to call readat() upon fileopen(), however.

Security: The defense layer should be robust against tampering and circumvention. Attackers must not be able to bypass, disable, or exploit the defense monitor's enhanced behaviors, ensuring the integrity and intended functionality of file operations.
