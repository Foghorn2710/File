begin
file = open("D:/akshay.txt","r")
words = Set{String}()

for line in eachline(file)
    for word in split(lowercase(line))
        push!(words, word)
    end
end

close(file)

println("Unique words are:")
for word in sort(collect(words))
    println(word)
end
end
