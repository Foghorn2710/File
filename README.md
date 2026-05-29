function freq_letter(text::String)
    freq = Dict{Char, Int}()

    text = lowercase(text)

    for char in text
        if 'a' <= char <= 'z'
            freq[char] = get(freq, char, 0) + 1
        end
    end

    for char in 'a':'z'
        count = get(freq, char, 0)
        println("$char : $count")
    end
end

println("Enter a text:")
text = readline()
freq_letter(text)
