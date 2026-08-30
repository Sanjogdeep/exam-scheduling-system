# Smart Exam Seating & Timetable Allocator — Final Submission

## What's in this folder

| File | What it is |
|---|---|
| `allocator.cpp` | The complete C++17 program — single file, no other source files needed |
| `data/students.csv`, `data/subjects.csv`, `data/rooms.csv` | Sample input data |
| `exam_seating_visualizer.html` | Visual seating-chart viewer (opens in any browser, no install) |
| `Project_Report.docx` | Full written report for submission |

## How to run it (Windows)

1. Extract this zip anywhere, e.g. `D:\final_submission`
2. Open PowerShell in that folder
3. Compile (only needed once, or after you edit the code):
   ```powershell
   g++ -std=c++17 -Wall -Wextra -O2 allocator.cpp -o allocator.exe
   ```
4. Run it:
   ```powershell
   .\allocator.exe
   ```
5. View the report:
   ```powershell
   type output\report.txt
   ```

This creates an `output` folder (automatically, even if it doesn't exist yet) containing `report.txt` and `report.json`.

## Do you need to run it "again and again" for the examiner?

**No — you only need to run it once before your demo**, and once more *live* if you want to prove it works in front of them. Here's the actual logic:

- The program's output doesn't change between runs **unless you change the CSV data**. Running it 5 times in a row with the same `students.csv`/`subjects.csv`/`rooms.csv` produces the exact same `report.txt` and `report.json` every time — there's no randomness in any of the algorithms.
- So for your demo, you have two reasonable options:
  1. **Run it once beforehand**, and just show the already-generated `output\report.txt` — completely fine, no need to re-run live.
  2. **Run it once live** in front of the examiner (`.\allocator.exe`), to prove it isn't a fake pre-written file — this only takes a second since the program runs instantly.

- The **only** time you'd need to rerun it is if you want to demonstrate that the program is data-driven — e.g. adding a new student to `students.csv` and showing the timetable/seating recompute correctly. That's a good thing to do *once* for effect, not something you need to repeat.

- If you also want to show the HTML visualizer: run `.\allocator.exe` once (so `output\report.json` exists), then open `exam_seating_visualizer.html` and load that JSON file. You don't need to rerun the C++ program again just to look at the visualizer afterward — the JSON file stays on disk until you overwrite it by running the program again.

## Quick demo script

```powershell
cd D:\final_submission
g++ -std=c++17 -Wall -Wextra -O2 allocator.cpp -o allocator.exe   # once
.\allocator.exe                                                   # run live for the examiner
type output\report.txt                                            # show the result
```

Then optionally open `exam_seating_visualizer.html`, click "Load your report.json", and select `output\report.json`.
