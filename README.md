# Code Jam 6: Qualifier

- **Deadline:** 2020-01-10 12:00 UTC
- **Submission form:** https://forms.gle/MzzZs9mFMKe2bwP77

The qualifier task for the upcoming Winter Code Jam is to write an [ISO-8601 timestamp](https://www.iso.org/iso-8601-date-and-time-format.html) parser function. We have provided you with a stub function in [qualifier.py](./qualifier.py) and it is your job to write the function body. To qualify for the code jam, your function needs to pass all of the basic requirements listed below. Additional points will be awarded if your function also passes any of the advanced requirements.

**You must write all the parsing from scratch. Using any kind of datestring parsing feature in your solution, either from a third party or a standard library module, will disqualify you from joining the Code Jam.**

While you are allowed to rewrite the docstring of the function, please make sure to keep the [function signature](https://www.pythonlikeyoumeanit.com/Module2_EssentialsOfPython/Functions.html#The-def-Statement) as it is.

### Basic Requirements
  - Must return an instance of `datetime.datetime` that is equivalent to the given ISO-8601 timestamp
  - Must be able to parse date strings in the format `YYYY-MM-DD`
  - Must also be able to parse combined datetime strings in the format `<date>T<time>`, where `<time>` can be one of:
     - `hh:mm:ss`  (e.g. `2017-05-05T12:00:00`)
     - `hh:mm`     (e.g. `2017-05-05T12:00`)
     - `hh`        (e.g. `2017-05-05T12`)
  - If given invalid input, raise a `ValueError` explaining what went wrong.

### Advanced Requirements (optional, for extra points)
  - Support the truncated date format `YYYYMMDD`
  - Support fractional seconds `hh:mm:ss.sss`
  - Support the truncated time formats `hhmmss.ssss`, `hhmmss`, `hhmm`
  - [Support time zones](https://en.wikipedia.org/wiki/ISO_8601#Time_zone_designators)
    - Timestamps without a timezone are local time
    - Timestamps with a timezone are relative to the UTC
      - Supported formats are `Z`, `±hh:mm`, `±hhmm` and `±hh`

## Examples
To pass all basic requirements, your function should behave the same as in these examples:
```py
>>> parse_iso8601("2019-12-16")
datetime.datetime(2019, 12, 16, 0, 0)
>>> parse_iso8601("2017-01-08T12")
datetime.datetime(2017, 1, 8, 12, 0)
>>> parse_iso8601("2008-12-03T08:15")
datetime.datetime(2008, 12, 3, 8, 15)
>>> parse_iso8601("1991-02-20T11:23:58")
datetime.datetime(1991, 2, 20, 11, 23, 58)
>>> parse_iso8601("2000-10-16T09:23:61")
Traceback (most recent call last):
  File "<stdin>", line 7, in parse_iso8601
ValueError: Invalid value for seconds
```

## Notes
- Due to the limitations of Python's `datetime` module, some dates specified in the ISO-8601 standard are impossible to be represented as a `datetime.datetime`. Therefore, those formats have not been included in the challenge.

- We are aware that `datetime.datetime` has a built-in classmethod, `datetime.fromisostring`, to parse ISO-8601 timestamps. Since it is your task to write a parser, using the built-in parser will lead to you not passing the qualifier.