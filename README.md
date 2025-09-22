# JsonDiffPatch for GameMaker Studio 2

Native JSON diff/patch/unpatch for GameMaker Studio 2 using a fast C++ DLL.

This extension wraps the [JsonDiffPatch C++ library](https://github.com/swompythesecond/jsondiffpatch-cpp)  
and exposes it to GameMaker Studio 2 via three simple functions:

- `JDP_Diff(leftJson, rightJson)` – Compute a diff between two JSON strings.
- `JDP_Patch(leftJson, diff)` – Apply a diff to get the patched JSON.
- `JDP_Unpatch(rightJson, diff)` – Reverse a diff to restore the original JSON.

---

## 📦 Download

[⬇️ Download the latest JsonDiffPatchGamemakerExtension.yymps](https://github.com/yourusername/jsondiffpatch-gamemaker/raw/main/JsonDiffPatchGamemakerExtension.yymps)

(or build the DLL yourself from the [C++ repo](https://github.com/swompythesecond/jsondiffpatch-cpp))

The prebuilt DLL for Windows is in [`bin/windows/JsonDiffPatchDLL.dll`](bin/windows/JsonDiffPatchDLL.dll).

---

## 🚀 Installation

1. Download `JsonDiffPatchGamemakerExtension.yymps` from this repository (link above).
2. In **GameMaker Studio 2**, go to `Tools > Import Local Package`.
3. Select the `.yymps` file. The extension and DLL will be added to your project automatically.
4. Make sure the extension is enabled for the **Windows** platform in the Extension Properties.

---

## 📝 Usage

Example script in GameMaker:

```gml
// Test 1: Empty strings
var diff1 = JDP_Diff("", "");
show_debug_message("Diff1: " + diff1);
var patched1 = JDP_Patch("", diff1);
show_debug_message("Patched1: " + patched1);
var unpatched1 = JDP_Unpatch("", diff1);
show_debug_message("Unpatched1: " + unpatched1);

// Test 2: Simple object change
var a = "{\"x\":1,\"y\":2}";
var b = "{\"x\":1,\"y\":3}";
var diff2 = JDP_Diff(a, b);
show_debug_message("Diff2: " + diff2);
var patched2 = JDP_Patch(a, diff2);
show_debug_message("Patched2: " + patched2);
var unpatched2 = JDP_Unpatch(b, diff2);
show_debug_message("Unpatched2: " + unpatched2);

// Test 3: Adding a field
var a3 = "{\"x\":1,\"y\":2}";
var b3 = "{\"x\":1,\"y\":2,\"z\":5}";
var diff3 = JDP_Diff(a3, b3);
show_debug_message("Diff3: " + diff3);
var patched3 = JDP_Patch(a3, diff3);
show_debug_message("Patched3: " + patched3);
var unpatched3 = JDP_Unpatch(b3, diff3);
show_debug_message("Unpatched3: " + unpatched3);

// Test 4: Array change
var a4 = "[1,2,3,4]";
var b4 = "[1,2,5,4]";
var diff4 = JDP_Diff(a4, b4);
show_debug_message("Diff4: " + diff4);
var patched4 = JDP_Patch(a4, diff4);
show_debug_message("Patched4: " + patched4);
var unpatched4 = JDP_Unpatch(b4, diff4);
show_debug_message("Unpatched4: " + unpatched4);

// Test 5: String change
var a5 = "\"Hello world\"";
var b5 = "\"Hello chatGPT\"";
var diff5 = JDP_Diff(a5, b5);
show_debug_message("Diff5: " + diff5);
var patched5 = JDP_Patch(a5, diff5);
show_debug_message("Patched5: " + patched5);
var unpatched5 = JDP_Unpatch(b5, diff5);
show_debug_message("Unpatched5: " + unpatched5);
