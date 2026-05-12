# Command-line `diff` and `patch` examples

## Example A: Use `diff` to compare two files

Two people have been working on a project, Anna and Fred.  Anna starts the project, and sends a copy to Fred to add his section.  Fred now wants to check his changes, so he creates a `diff` of the two files.

```bash
diff -Naur anna fred
```

```diff
diff -Naur anna/new-folder/freds-new-file.md fred/new-folder/freds-new-file.md
--- anna/new-folder/freds-new-file.md	1970-01-01 01:00:00.000000000 +0100
+++ fred/new-folder/freds-new-file.md	2026-05-12 10:05:55.579007737 +0100
@@ -0,0 +1,3 @@
+# Fred added this file
+
+Hello World!
diff -Naur anna/sample.md fred/sample.md
--- anna/sample.md	2026-05-12 09:06:38.277399757 +0100
+++ fred/sample.md	2026-05-12 10:15:25.348107299 +0100
@@ -1,3 +1,7 @@
 # Sample

-This is Anna's version.  She had the original idea.
+This is Fred's version.  He changed this line.
+
+## Heading 2
+
+Fred added some more text here about something else.
```

You can see the lines that have been changed, `-` (red) indicates line removed, `+` (green)indicates line added.  The `-Naur` are the `diff` command options that are most like the method Git uses.

## Example B: Create and apply a patch

Fred wants to send his changes to Anna, but doesn't want to send a complete copy of all of the whole project.  Instead, he creates a `patch` file and sends that instead.

```bash
# Create patch file from original -> updated
diff -Naur anna fred > update.patch
```

This command does the same `diff -Naur` command we used before but pipes the output into a file called `update.patch`.

Fred sends the patch file to Anna and she applies it to her work.

Anna copies her work into a new directory, `anna2`.

```bash
cp -r anna anna2
```

Applies the patch.

```bash
# Changed directory
cd anna2
# Check what files are present.
ls -R
# Apply the patch
patch -p1 < ../update.patch
# See what's changed.
ls -R
# Print contents of the modified files
cat sample.md
cat new-folder/freds-new-file.md
```

Show this repo in `gitk` to show the `diffs` and branches.
