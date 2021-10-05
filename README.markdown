# govuk-pay-rota-generators

This generates a support rota for GOV.UK Pay. This repo has been forked from [govuk-rota-generators](https://github.com/barrucadu/govuk-rota-generators).

## Setting up

* Follow instructions at https://github.com/coin-or/Cbc to download cbc.
* You also need `python3` and `pip3`.
* Run `pip3 install -r requirements.txt`

## How to use
```
$ python3 src
Usage:
  cli.py <file> [--num-weeks=<n>] [--max-in-hours-shifts=<n>] [--max-on-call-shifts=<n>]
  cli.py (-h | --help)

$ time python3 src govuk_pay_people.csv --max-in-hours-shifts=1 --max-on-call-shifts=2 --num-weeks=12
week,primary,primary_oncall,secondary_oncall
1,Grant Kornfeld,Oswaldo Bonham,Bessie Engebretson
2,Martin Ashby,Jarrett Hord,Santiago Raine
3,Renae Paton,Oswaldo Bonham,Emanuel Leinen
4,Bessie Engebretson,Chas Stucky,Harry Poopoo
5,Santiago Raine,Jarrett Hord,Jame Truss
6,Emanuel Leinen,Harry Poopoo,Ryan Averett
7,Neil Hockenberry,Martin Ashby,Bessie Engebretson
8,Ryan Averett,Sammie Shew,Santiago Raine
9,Jarrett Hord,Jame Truss,Martin Ashby
10,Chas Stucky,Sammie Shew,Renae Paton
11,Harry Poopoo,Grant Kornfeld,Neil Hockenberry
12,Oswaldo Bonham,Chas Stucky,Emanuel Leinen
        0.74 real         0.62 user         0.06 sys
```

See the `docs` directory for explanations of how the rotas are defined
and generated.

### Mathematical background

This uses an approach called [integer linear programming][] (ILP), via
the [PuLP library][].  A reasonable introduction to ILP for solving
scheduling problems like this is [the PyCon conference-scheduler
docs][].

I [wrote a memo][memo] going into some detail about how it all works.

[integer linear programming]: https://en.wikipedia.org/wiki/Integer_programming
[PuLP library]: https://pythonhosted.org/PuLP/
[the PyCon conference-scheduler docs]: https://conference-scheduler.readthedocs.io/en/latest/background/mathematical_model.html
[memo]: https://memo.barrucadu.co.uk/scheduling-problems.html
