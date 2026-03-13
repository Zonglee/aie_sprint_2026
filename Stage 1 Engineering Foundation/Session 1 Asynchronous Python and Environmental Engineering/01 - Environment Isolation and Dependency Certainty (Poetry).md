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
		- `Poetry` will scan all your dependencies and create a **Dependency Graph**.  It will **ONLY** install the version of a dependency which falls in the **union set** of all the requirements of your projects. (**Global Dependencies Resolution**)
			- For instance, Project A requires `numpy ^2.1.0` and Project B requires `numpy ~2.1.0`. The union set of `numpy` will be \[2.1.0, 2.1.9). `Poetry` will install `numpy` which version falls between the union set, for example, `numpy 2.1.3`. (If you are not familiar with the signs here, please refer to [[Appendix 1 - Dependency Specification Identifiers]] )
			- What if the requirements of my projects don't have a union set? For example, Project A requires `numpy >= 1.20` while Project B requires `numpy < 1.19`.  At this point, Poetry will abort the process.
				- **Solution A: Isolation (Best Practice🥳)**. If Project A and B are two independent task or model, then **never put them in the same Poetry project**. Execute `poetry init` separately for each project folder.
				- **Solution B: Compromization**: If you unfortunately have to use project A and B at the same time, you can find the latest version of B to see if it support higher version of `numpy`, or you can find an alternate for Project B, or you can downgrade the Project A if A support lower versions of `numpy`.
				- **Solution C: Microservices / Containerization:** If you are doing something big, for instance, an AI system, you can containerize Project A and B, and let them communicate through APIs. (For example, FastAPI, we will expand on it in the next session. *\[\[Insert link here, or not.\]\]*)
				  We will expand on the containerization stuff later. 
				- **Solution D: Vendoring (or being crazy?):** Download the whole resource codes and rewrite it. Seriously, how desperate/fancy/\[insert cuter words here\] are you?
> [!note] Nerd Alert!!
> **What's the difference between Parsing and Resolution?**
> - *Parsing* emphasizes on "read and understand". The word "understand" refers to generate something the stupid computers can read. To `Poetry`, it's the Dependency Graph.
> - *Resolution* refers to "correlate" and "calculate".  The process of `Poetry` calculating the right version is called resolution. The process of a certain algorithm calculate the address is called resolution.

After finishing reading this, you can try to install `Poetry` on your computer.
## 2.2 Basic Usage

> [!error] Objectives
> Learn how to `new` a project, and `add` a package like `numpy`.

Please refer to the [Official Tutorial](https://python-poetry.org/docs/basic-usage/). It provides with a very detailed and step-by-step guidance.

