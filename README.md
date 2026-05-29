function pop_artist()
    artist = Vector{String}(undef, 10)

    println("Enter the names of 10 pop artists:")
    for i in 1:10
        print("Enter the name of artist $i: ")
        artist[i] = readline()
    end

    votes = Dict{Int, Int}()

    for i in 1:10
        votes[i] = 0
    end

    println("Enter the votes (a number between 1 and 10).")
    println("Enter 'end' to stop voting:")

    while true
        vote = readline()

        if vote == "end"
            break
        end

        vote_number = tryparse(Int, vote)

        if vote_number !== nothing && 1 <= vote_number <= 10
            votes[vote_number] += 1
        else
            println("Invalid vote. Enter a number between 1 and 10.")
        end
    end

    println("\nVoting Results:")
    for i in 1:10
        println("$(artist[i]) : $(votes[i]) votes")
    end
end

pop_artist()
