# [Julia][julialang]
## `String` Manipulation
### Generate markdown table from `Vector` inputs
```julia
function md_alignment(sym::Symbol)::String
    if sym == :c
        ":-:"
    elseif sym == :r
        "--:"
    else
        ":--"
    end
end
```

```julia
md_table_row(X)::String = "|$(join(X,"|"))|"
```

```julia
function markdown_table(arr::Vector, headers::Vector, alignments::Vector{Symbol}=Symbol[])::String
    arr_element_lens = length.(arr) |> unique

    length(arr_element_lens) == 1 || error("Multiple tuple lengths in array")
    arr_element_lens[1] == length(headers) || error("Tuple and header length differ")

    arr = md_table_row.(arr)

    if !isempty(alignments)
        arr_element_lens[1] == length(alignments) || error("Alignment vector differs in length from tuples or header")
        arr = append!([md_table_row(md_alignment.(alignments))], arr)
    else
        alignment_strings = md_alignment.(repeat([:l], arr_element_lens[1]))
        arr = append!([md_table_row(alignment_strings)], arr)
    end

    join(append!([md_table_row(headers)], arr), "\n")
end
```

## License
<a rel="license" href="http://creativecommons.org/licenses/by-nc/4.0/"><img alt="Creative Commons License" style="border-width:0" src="https://i.creativecommons.org/l/by-nc/4.0/88x31.png" /></a><br />This work is licensed under a <a rel="license" href="http://creativecommons.org/licenses/by-nc/4.0/">Creative Commons Attribution-NonCommercial 4.0 International License</a>.

[julialang]: https://www.julialang.org/
