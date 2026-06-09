## Challenge: Collaborative Development

**Author:** Jeffery John

**Category:** General Skills

### Core Concept

This challenge introduces the fundamentals of **Git Version Control** and team workflows. In a professional development environment, engineers don't work on the same main file at the same time; doing so would cause constant conflicts. Instead, they use Git to branch off, create their features independently, and later merge them back together.

Here, the team split the flag production into three separate "feature branches." To see the final product, you have to play the role of the project manager and integrate everyone's code.

### Toolbox

- **unzip:** To extract the workspace files.
- **git branch:** To list all local branches in the repository.
- **git checkout:** To switch between different version branches.
- **git merge:** To combine the histories and code changes from separate branches into your current branch.

### Methodology

1. **Repository Extraction:** You unzipped `challenge.zip` and noticed a standard project directory containing a Python script (`flag.py`). Reading it on the `main` branch showed that the code was incomplete.
2. **Exploring the Branches:** Recognizing the word "Collaborative" in the title as a hint for version control, you checked for hidden Git metadata. Running `git branch -a` (or `git branch`) revealed that the team had been busy on three distinct tracks:

- `feature/part-1`
- `feature/part-2`
- `feature/part-3`

3. **Code Inspection:** You switched over to each branch using `git checkout <branch_name>` to verify their progress. Each branch contained a different piece of the script puzzle.
4. **Integrating the Code:** To reconstruct the full application, you returned to your primary workspace (`git checkout main`) and systematically merged the features:

```bash
git merge feature/part-1
git merge feature/part-2
git merge feature/part-3

```

5. **Execution:** With all parts cleanly merged into `main`, you ran the completed script using `python3 flag.py` to print out the fully assembled flag.

---

### My Insight

Using `git merge` is the textbook way to handle this, and it mimics an actual software development pipeline perfectly!

If you ever run into a similar challenge where Git conflicts stop you from merging smoothly, or you just want to grab the data quickly without messing with the repository history, you can read files from other branches directly without switching your active workspace.

You can use the **`git show`** command to peek into alternative branches instantly:

```bash
git show feature/part-1:flag.py
git show feature/part-2:flag.py
git show feature/part-3:flag.py

```

This prints out what `flag.py` looks like inside each respective branch right to your screen, letting you piece the flag together manually in your notes if you're in a rush!
