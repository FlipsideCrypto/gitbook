# Osmosis Dim Vote Options

### Table Schema

`osmosis.core.dim_vote_options`

Join this table to `osmosis.fact_governance_votes` on `vote_option = vote_id`

| Field       | Type    | Description                                          |
| ----------- | ------- | ---------------------------------------------------- |
| vote\_id    | integer | Numeric option that corresponds to the user's vote.  |
| description | string  | Text that describes the vote option.                 |
