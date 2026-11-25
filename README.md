git clone <your repository URL> changelens
cd changelens
Set-ExecutionPolicy -Scope Process -ExecutionPolicy Bypass
py -3 -m venv .venv
.venv\Scripts\Activate.ps1
python -m pip config --site set global.index-url https://artifactory.schwab.com/artifactory/api/pypi/python-pypi-remote/simple
python -m pip install --upgrade pip
python -m pip install -r requirements.lock
python -m pip install --no-deps -e .
copy .env.example .env

git add README.md
git commit -m "README: install steps work on the company network" -m "- Point pip at the company mirror before the first pip install (pip upgrade included),
  on Windows and macOS/Linux
- Windows: execution policy set for the current window only (Process, Bypass)
- Use python -m pip after activating the venv; py -3 only to create it"
git push