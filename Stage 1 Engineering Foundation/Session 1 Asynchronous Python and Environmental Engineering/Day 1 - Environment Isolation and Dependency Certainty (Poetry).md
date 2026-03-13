# 1. Getting Started 
**Problem Spotted**: The codes can be run locally, but when it's uploaded to the server / shared with others, it's problematic.

**Solution:** ✨Poetry✨

**Objectives:**
1. Know the difference between `pyproject.toml` and `poetry.lock`
	1. Why `.lock` file must be submitted to Git?
2. Know the difference between `poetry shell` and `poetry run`
3. Dependency Decoupling: Dev vs. Production (Dependency Groups)

  **Resources:**
  1. [Poetry Documentation](https://python-poetry.org/docs/) 

# 2.  Quick Warming Up
## 2.1 [Introduction](https://python-poetry.org/docs/)
- What can Poetry do? 
	- It can declare the dependencies your project use and *manage* them (update/install) for you.
- How does Poetry manage dependencies?
	- Use `lockfile`.
- Why don't I just use `pip`?
	- **`pip`'s Limitation: Greedy Search**
		- For instance, you've installed `numpy 1.26` when installing `Project A`. But later, if you install `Project B` which needs `numpy 1.23`, `pip` will cover the previous version of `numpy`, which is `numpy 1.26`, and that will lead to A not working.
	- **`Poetry`'s Logic: Global Parsing**
		- `Poetry` will scan all your dependencies and create a **Dependency Graph**.  It will **ONLY** install the version of a dependency which falls in the **union set** of all the requirements of your projects.
			- 