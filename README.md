# Pizza Validator

A validator for the **Pizza** problem from the Google Hash Code 2017 practice round.

Given a pizza grid and a proposed set of slices, this tool checks whether the solution is valid and reports its score.

## What it checks

For each slice in the result file, the validator verifies that:

- the slice area does not exceed the maximum cell limit `H`;
- the slice lies entirely within the pizza grid;
- slices do not overlap (collision detection);
- the slice contains at least `L` mushrooms and at least `L` tomatoes.

If every slice passes, it prints the total score (cells covered by valid slices) and the coverage ratio.

## Build

```sh
g++ -o validator validator.cpp
```

## Run

```sh
./validator <input_file> <result_file>
```

- `<input_file>` — the problem input: first line `R C L H` (rows, columns, min ingredient count, max slice area), followed by the `R × C` grid of `T` (tomato) and `M` (mushroom) cells.
- `<result_file>` — the solution: first line `S` (number of slices), then `S` lines of `r1 c1 r2 c2` describing each slice's top-left and bottom-right corners.

## Output

On success:

```
Validation successful, score is <total>, coverage is <ratio>
```

On failure, it prints the offending slice and the reason (area too large, out of bounds, collision, or too few ingredients) and exits with a non-zero status.

## Attribution

The validator is sourced from <https://github.com/JulianNeeleman/pizza/blob/master/tools/validator.cpp>.
