# Analysis Traceability

DeepResValue is not a "black box AI" — every analysis step is **fully transparent and traceable**, 100% reproducible.

## Why It Matters

When defense committee members ask "How did you get this result?" — you can display the complete analysis path and code on the spot, proving the reliability of your results.

## What's Preserved

### Complete Code & Logs

After each analysis task, you can review:

- **Complete Python/R code**: Every line of code the AI executed is preserved
- **Execution logs**: Runtime status and intermediate results at each step
- **Data lineage**: The complete chain from input → cleaning → analysis → output

### Sub-Task Cards

Complex tasks are automatically decomposed into sub-tasks displayed as collapsible cards:

1. Each card shows the sub-task name (e.g., "Search related literature", "Execute data cleaning")
2. Click **▶ Expand** to view detailed process and results for that sub-task
3. After all sub-tasks complete, the AI aggregates and outputs the final conclusion

### Tool Call Visualization

During AI analysis, you can see in real time which tools it invokes:

| Panel | Displayed Content |
|-------|-------------------|
| **Search Panel** | Number of sources found and summaries during web search |
| **Code Execution Panel** | Code content, runtime status, and output during Python execution |
| **File Read Indicator** | Filename and parsing progress when reading uploaded files |

## Viewing the Analysis Process

1. **Send an analysis request** — Enter your analysis needs normally; the AI begins execution.
2. **Observe in real time** — During analysis, the interface shows tool calls, code execution, search results, and other intermediate steps in real time.
3. **Expand detailed logs** — After analysis completes, click each sub-task card to expand and view the complete code and execution logs.

> All analysis processes are permanently saved in conversation history, viewable at any time. During defense, you can directly display the complete evidence chain — 100% reproducible.

> If you need to include the analysis process as a thesis appendix, consider screenshotting the key code panels and execution results.
