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

        if vote_number !== nothing && vote_number >= 1 && vote_number <= 10
            votes[vote_number] += 1
        else
            println("Invalid vote, please try a number between 1 and 10.")
        end
    end

    max_votes = 0
    most_pop_artist = ""

    for i in 1:10
        if votes[i] > max_votes
            max_votes = votes[i]
            most_pop_artist = artist[i]
        end
    end

    if max_votes > 0
        println("The most popular artist is: $most_pop_artist with $max_votes votes.")
    else
        println("No votes were cast.")
    end
end

pop_artist()
