# MLOps Projekt
Numer albumu: 99788
## Porównanie narzędzi do zarządzania środowiskiem i danymi

| Narzędzie | Zmierzony czas instalacji | Plik definicji zależności | Odtworzenie środowiska jedną komendą | Kiedy stosować (Rekomendacja) |
| :--- | :--- | :--- | :--- | :--- |
| **venv** | ~18.5 s | `requirements.txt` | `pip install -r requirements.txt` | Standardowe, proste projekty w czystym Pythonie bez skomplikowanych zależności systemowych; środowiska, w których nie można instalować zewnętrznych narzędzi. |
| **uv** | **3.09 s** | `requirements.txt` / `pyproject.toml` | `uv pip install -r requirements.txt` (lub `uv sync`) | Nowoczesne projekty Python i pipeline'y CI/CD (np. Docker, GitHub Actions), gdzie kluczowa jest maksymalna prędkość budowania środowiska. |
| **Conda** | ~35.0 s | `environment.yml` | `conda env create -f environment.yml` | Projekty Data Science / Deep Learning wymagające bibliotek spoza ekosystemu Pythona (C/C++, MKL), kompilatorów oraz wsparcia dla GPU (CUDA). |
| **DVC** | *N/D (narzędzie danych)* | `*.dvc` (np. `data/housing.csv.dvc`), `.dvc/config` | `dvc pull` | Wersjonowanie dużych zbiorów danych i modeli ML. W odróżnieniu od Gita, przechowuje właściwe pliki w zewnętrznym magazynie (remote), a w repozytorium zapisuje jedynie lekkie pliki-wskaźniki z sumami kontrolnymi (MD5). |
