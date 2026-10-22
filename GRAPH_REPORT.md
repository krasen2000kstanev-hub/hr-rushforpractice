# Graph Report - hr-rushforpractice  (2026-10-22)

## Corpus Check
- cluster-only mode — file stats not available

## Summary
- 59 nodes · 164 edges · 8 communities (5 shown, 3 thin omitted)
- Extraction: 99% EXTRACTED · 1% INFERRED · 0% AMBIGUOUS · INFERRED: 1 edges (avg confidence: 0.85)
- Token cost: 0 input · 0 output

## Graph Freshness
- Built from commit: `eec41930`
- Run `git rev-parse HEAD` and compare to check if the graph is stale.
- Run `graphify update .` after code changes (no API cost).

## Community Hubs (Navigation)
- app.py
- ApiError
- dispatch
- user_id
- test_app.py
- review
- app.js

## God Nodes (most connected - your core abstractions)
1. `dispatch()` - 21 edges
2. `ApiError` - 15 edges
3. `public_item()` - 12 edges
4. `user_id()` - 12 edges
5. `submit()` - 11 edges
6. `create_mission()` - 10 edges
7. `review()` - 10 edges
8. `get_item()` - 9 edges
9. `now()` - 9 edges
10. `body()` - 8 edges

## Surprising Connections (you probably didn't know these)
- `dispatch()` --calls--> `ApiError`  [EXTRACTED]
  backend/app.py → backend/app.py  _Bridges community 1 → community 2_
- `get_mission()` --calls--> `ApiError`  [EXTRACTED]
  backend/app.py → backend/app.py  _Bridges community 1 → community 3_
- `review()` --calls--> `ApiError`  [EXTRACTED]
  backend/app.py → backend/app.py  _Bridges community 1 → community 5_
- `handler()` --calls--> `dispatch()`  [EXTRACTED]
  backend/app.py → backend/app.py  _Bridges community 0 → community 2_
- `body()` --calls--> `json`  [EXTRACTED]
  backend/app.py →   _Bridges community 1 → community 0_

## Import Cycles
- None detected.

## Communities (8 total, 3 thin omitted)

### Community 0 - "app.py"
Cohesion: 0.24
Nodes (5): decimal_default(), handler(), method(), path(), response()

### Community 1 - "ApiError"
Cohesion: 0.38
Nodes (7): add_team_member(), ApiError, body(), clean_id(), create_mission(), create_team(), require_role()

### Community 2 - "dispatch"
Cohesion: 0.47
Nodes (10): dispatch(), get_missions(), get_team(), leaderboard(), my_submissions(), notifications(), points_history(), public_item() (+2 more)

### Community 3 - "user_id"
Cohesion: 0.39
Nodes (9): claims(), ensure_profile(), get_item(), get_mission(), mark_notification(), roles(), submission(), submit() (+1 more)

### Community 5 - "review"
Cohesion: 0.60
Nodes (4): approve_transaction(), notify(), now(), review()

## Knowledge Gaps
- **3 thin communities (<3 nodes) omitted from report** — run `graphify query` to explore isolated nodes.

## Suggested Questions
_Questions this graph is uniquely positioned to answer:_

- **Why does `ApiError` connect `ApiError` to `app.py`, `dispatch`, `user_id`, `review`?**
  _High betweenness centrality (0.060) - this node is a cross-community bridge._
- **Why does `dispatch()` connect `dispatch` to `app.py`, `ApiError`, `user_id`, `review`?**
  _High betweenness centrality (0.046) - this node is a cross-community bridge._
- **Why does `user_id()` connect `user_id` to `app.py`, `ApiError`, `dispatch`, `review`?**
  _High betweenness centrality (0.013) - this node is a cross-community bridge._