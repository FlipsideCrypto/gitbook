# Dim Dates

### Table Schema

A utility table of common date constructs.

`crosschain.dim_dates`

| Field                               | Type   | Description                                                             |
| ----------------------------------- | ------ | ----------------------------------------------------------------------- |
| DATE\_DAY                           | DATE   | date for the row                                                        |
| PRIOR\_DATE\_DAY                    | DATE   | date before DATE\_DAY                                                   |
| NEXT\_DATE\_DAY                     | DATE   | date after DATE\_DAY                                                    |
| PRIOR\_YEAR\_DATE\_DAY              | DATE   | date exactly 1 year before DATE\_DAY                                    |
| PRIOR\_YEAR\_OVER\_YEAR\_DATE\_DAY  | DATE   | date exactly 1 year after DATE\_DAY                                     |
| DAY\_OF\_WEEK                       | NUMBER | number representing day of week for DATE\_DAY where 1=Sunday            |
| DAY\_OF\_WEEK\_ISO                  | NUMBER | number representing day of week for DATE\_DAY where 1=Monday            |
| DAY\_OF\_WEEK\_NAME                 | STRING | day of week name for DATE\_DAY                                          |
| DAY\_OF\_WEEK\_NAME\_SHORT          | STRING | day of week abbreviation for DATE\_DAY                                  |
| DAY\_OF\_MONTH                      | NUMBER | day of month for DATE\_DAY                                              |
| DAY\_OF\_YEAR                       | NUMBER | day of year for DATE\_DAY                                               |
| WEEK\_START\_DATE                   | DATE   | date representing the start of the week for DATE\_DAY                   |
| WEEK\_END\_DATE                     | DATE   | date representing the end of the week for DATE\_DAY                     |
| PRIOR\_YEAR\_WEEK\_START\_DATE      | DATE   | date representing the start of the week for PRIOR\_YEAR\_DATE\_DAY      |
| PRIOR\_YEAR\_WEEK\_END\_DATE        | DATE   | date representing the end of the week for PRIOR\_YEAR\_DATE\_DAY        |
| WEEK\_OF\_YEAR                      | NUMBER | number representing the week of the year for DATE\_DAY                  |
| ISO\_WEEK\_START\_DATE              | DATE   | ISO date representing the start of the week for DATE\_DAY               |
| ISO\_WEEK\_END\_DATE                | DATE   | ISO date representing the end of the week for DATE\_DAY                 |
| PRIOR\_YEAR\_ISO\_WEEK\_START\_DATE | DATE   | ISO date representing the start of the week for PRIOR\_YEAR\_DATE\_DAY  |
| PRIOR\_YEAR\_ISO\_WEEK\_END\_DATE   | DATE   | ISO date representing the end of the week for PRIOR\_YEAR\_DATE\_DAY    |
| ISO\_WEEK\_OF\_YEAR                 | NUMBER | number representing the ISO week of the year for DATE\_DAY              |
| PRIOR\_YEAR\_WEEK\_OF\_YEAR         | NUMBER | number representing the week of the year for PRIOR\_YEAR\_DATE\_DAY     |
| PRIOR\_YEAR\_ISO\_WEEK\_OF\_YEAR    | NUMBER | number representing the ISO week of the year for PRIOR\_YEAR\_DATE\_DAY |
| MONTH\_OF\_YEAR                     | NUMBER | number representing the month of the year for DATE\_DAY                 |
| MONTH\_NAME                         | STRING | month of year name for DATE\_DAY                                        |
| MONTH\_NAME\_SHORT                  | STRING | month of year abbreviation for DATE\_DAY                                |
| MONTH\_START\_DATE                  | DATE   | first date of month for DATE\_DAY                                       |
| MONTH\_END\_DATE                    | DATE   | last date of month for DATE\_DAY                                        |
| PRIOR\_YEAR\_MONTH\_START\_DATE     | DATE   | first date of month for PRIOR\_YEAR\_DATE\_DAY                          |
| PRIOR\_YEAR\_MONTH\_END\_DATE       | DATE   | last date of month for PRIOR\_YEAR\_DATE\_DAY                           |
| QUARTER\_OF\_YEAR                   | NUMBER | number representing quarter for DATE\_DAY                               |
| QUARTER\_START\_DATE                | DATE   | first date of quarter for DATE\_DAY                                     |
| QUARTER\_END\_DATE                  | DATE   | last date of quarter for DATE\_DAY                                      |
| YEAR\_NUMBER                        | NUMBER | number presenting the year for DATE\_DAY                                |
| YEAR\_START\_DATE                   | DATE   | first date of year for DATE\_DAY                                        |
| YEAR\_END\_DATE                     | DATE   | last date of year for DATE\_DAY                                         |
