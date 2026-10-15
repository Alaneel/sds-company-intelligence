# SDS Company Intelligence

**A datathon prototype for exploring company segmentation, scoring rules and generated explanations.**

Built in the context of SDS Datathon 2026, this Python project connects an analysis pipeline to a Streamlit dashboard. It combines exploratory clustering, heuristic scores, anomaly flags and optional Gemini-generated summaries.

## Read the implementation

| Component | Code | Purpose |
| --- | --- | --- |
| Analysis pipeline | [enhanced_analysis.py](src/enhanced_analysis.py) | Numeric cleaning, K-Means segmentation, scoring rules and Isolation Forest flags |
| New-company evaluation | [inference_engine.py](src/inference_engine.py) | Apply saved artifacts and scoring logic to an input company |
| Generated explanations | [llm_insights.py](src/llm_insights.py) | Gemini integration, prompts and mock/fallback responses |
| Dashboard | [app.py](src/app.py) | Explore segments, comparisons and analysis views |
| Further experiments | [scripts](scripts) | Statistical checks and validation experiments |
| Team context | [Collaboration guide](docs/COLLABORATION_GUIDE.md) | Existing project collaboration notes |

## Local development

Use only data you are authorized to process. The dashboard depends on the expected input schema and locally generated analysis artifacts; cloning the code is not sufficient to reproduce a complete run.

```bash
python3 -m venv .venv
source .venv/bin/activate
python -m pip install -r requirements.txt
# After preparing authorized inputs and the required analysis artifacts:
streamlit run src/app.py
```

The analysis entry point is `python src/enhanced_analysis.py`. The [demo runner](run_demo.sh) documents the expected sequence; run it with **Bash** because it uses Bash-specific syntax and interactive prompts. The requirements file is not a reproducible environment lock.

Gemini features use `GEMINI_API_KEY` from the local environment. Missing configuration or API failures can produce mock/fallback output; those responses must not be presented as successful model evaluations. Confirm permission to send any company data to an external model before enabling it.

## Interpretation limits

Clusters are exploratory groupings. Lead scores and risk flags encode assumptions in the code; they are not verified classifications of company conduct. In particular, a revenue/employee heuristic does not establish that an entity is a shell company. Generated summaries are not validated due-diligence reports.

Cluster counts and evaluation results depend on the input dataset and experiment configuration. Inspect inputs, splits, labels and generated artifacts before drawing conclusions.

## Source and data rights

The project references a Champions Group dataset and includes derived artifacts and reports. Confirm dataset terms, event agreements, team contributions and redistribution rights before sharing those materials; a code license does not automatically cover them.
