# Soko Bora 🌽 — Fair Market Prices for Every Farmer

**Tagline:** *Know your market before you sell.*

## Problem Statement

Smallholder farmers across East Africa frequently sell their produce at
whatever price the nearest buyer offers, because they have no easy way to
compare prices across nearby markets. Middlemen often exploit this
information gap, buying low from farmers who don't know that a market
30km away is paying significantly more for the same crop. Soko Bora
("good market" in Swahili) closes that information gap by letting
farmers, buyers, and field agents report and view real-time crop prices
across markets in their region.

## Target Users

- **Smallholder farmers** deciding where and when to sell their harvest
- **Buyers/traders** wanting visibility into fair regional pricing
- **Agricultural extension workers / NGOs** monitoring price trends to
  support farmer cooperatives

## Core Features

1. **Submit price reports** — any user can report a crop price observed
   at a specific market (crop, market, region, price per kg)
2. **Browse current prices** — view all reported prices, most recent first
3. **Filter by crop or region** — quickly compare, e.g., maize prices
   across all markets in Kigali
4. *(Planned — F2/F3)* Price trend charts over time per crop/region
5. *(Planned — F2/F3)* SMS/USSD access for farmers without smartphones

## Technology Stack

- **Backend:** Python 3.11, Flask, Flask-SQLAlchemy
- **Database:** PostgreSQL (production/Docker), SQLite (local/tests)
- **Testing:** pytest
- **Linting:** flake8
- **Containerization:** Docker, Docker Compose
- **CI/CD:** GitHub Actions
- *(Planned — later formatives)* Terraform for IaC, monitoring stack,
  microservices split (e.g., separating price-ingestion from
  price-query services)

## Project Structure

```
.
├── app/
│   ├── __init__.py
│   └── main.py              # Flask app, models, and routes
├── tests/
│   ├── __init__.py
│   └── test_main.py         # pytest test suite
├── requirements.txt
├── requirements-dev.txt
└── README.md
```

## Running Locally

```bash
python -m venv venv
source venv/bin/activate
pip install -r requirements-dev.txt
python app/main.py
```

On Windows PowerShell, use:

```powershell
py -m venv venv
.\venv\Scripts\Activate.ps1
python -m pip install -r requirements-dev.txt
python app/main.py
```

The API will be available at `http://localhost:5000`.

### Example usage

```bash
# Report a price
curl -X POST http://localhost:5000/api/prices \
  -H "Content-Type: application/json" \
  -d '{"crop_name": "Maize", "market_name": "Kimironko Market", "region": "Kigali", "price_per_kg": 350, "reported_by": "farmer_jane"}'

# List all prices
curl http://localhost:5000/api/prices

# Filter by region
curl "http://localhost:5000/api/prices?region=Kigali"
```

## Running Tests

```bash
pytest tests/ -v
flake8 app tests --max-line-length=100
```

## Team

Add your team member names, roles, and participation notes here before
submission. A simple format that works well for the assignment is:

| Name | Role | Contribution |
| --- | --- | --- |
| Team member 1 | Backend Lead | Implemented the Flask API and core price reporting feature |
| Team member 2 | DevOps Lead | Managed the repo setup, `.gitignore`, and branch protection |
| Team member 3 | QA / Docs Lead | Wrote tests, README setup notes, and board items |
| Team member 4 | Frontend / Product Lead | Refined the project scope and user stories |

Update the table with your real group members before you submit the repo.

## Project Board

See the GitHub Projects Kanban board linked in the repository description
for the current backlog, in-progress work, and completed items. See
`PROJECT_BOARD.md` in this repo for the initial backlog content used to
seed that board.

## Submission Checklist

- Add the final team member names and roles in the table above.
- Make sure the GitHub Projects board has at least 8-10 items and uses
  Backlog, In Progress, and Done columns.
- Confirm branch protection is enabled on `main` in GitHub settings.
- Add the repository URL and team participation sheet to the Canvas
  submission.

Munezero Hubert