This is designed for team collaboration and keeps things reproducible and clean 👇

⸻

# 🧩 Prerequisites

Before setting up the environment, make sure Conda is installed on your system.

You can use either:
    <br>
	• 🐍 Miniconda — lightweight, recommended
    <br>
	• 🧬 Anaconda — includes Conda plus many preinstalled packages

Check if Conda is already installed:

```Bash
conda --version
```

You should see something like:

```Bash
conda 24.3.1
````

✅ Any modern version of Conda (≥ 23.x) works fine for this project.
If you don’t have it, install Miniconda from the link above before proceeding.

⸻

<br>

# ⚙️ Environment Setup and Updates (Conda)

1️⃣ Create and activate the environment

Use the provided environment.yml file to create the Conda environment:

```Bash
conda env create -f environment.yml
conda activate stats500
```

If the environment already exists and you just pulled updates from GitHub, run:

```Bash
conda env update -f environment.yml --prune
```

This ensures your environment matches the latest version in the repository.

⸻

2️⃣ Add a new package

If you need to install a new library for your work:

```Bash
conda activate stats500
```

Then install the package using Conda (preferred):

```Bash
conda install package-name
```

If the package isn’t available through Conda, you can install it with pip:

```Bash
pip install package-name
```

After verifying the package works, proceed to update the shared environment file.

⸻

3️⃣ Update and share the environment file

After installing new packages, re-export the environment so others can stay in sync.


```Bash
# macOS 
conda env export --from-history --no-builds > environment.yml
sed -i '' '/^prefix:/d' environment.yml  

# PC 
conda env export --from-history --no-builds | Select-String -NotMatch '^prefix:' | Out-File -Encoding utf8 environment.yml
```

Then commit and push your changes to GitHub:

```Bash
git add environment.yml
git commit -m "Add new package(s) to environment.yml"
git push
```

⸻

4️⃣ Update your environment after others make changes

If a teammate adds new packages and pushes an updated environment.yml, you can pull the changes and update your own environment:

```Bash
git pull
conda env update -f environment.yml --prune
```

⸻

✅ Best practices
<br>
	•	Always activate the correct environment before installing packages.
 <br>
	•	Use conda install when possible — fall back to pip only when necessary.
 <br>
	•	Re-export and commit the updated environment.yml after installing new packages.
 <br>
	•	Never manually edit the YAML — let Conda generate it for you.
 <br>
	•	Use --from-history to keep the file minimal and cross-platform compatible.