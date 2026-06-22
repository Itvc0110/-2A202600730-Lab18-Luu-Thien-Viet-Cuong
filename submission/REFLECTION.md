# Reflection

Luu Thien VIet Cuong  
Student ID: 2A202600730

The anti-pattern my team would be most at risk of is ignoring OPTIMIZE until the small-file problem becomes painful. In this lab, NB2 showed how 200 small files made a simple filtered query slower, while compaction plus Z-ORDER reduced the file count and tightened min/max stats so Delta could skip irrelevant files.

This is easy to miss in real projects because streaming or frequent appends look correct at first: data lands, dashboards refresh, and nobody notices the performance tax until the table grows. For LLM observability logs, request data arrives continuously, so I would schedule regular OPTIMIZE, monitor file counts, and choose date partitioning with Z-ORDER on hot filter columns instead of partitioning by high-cardinality fields like user_id.
