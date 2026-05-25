begin
print("Enter the principal amount (P):")
p=parse(Float64,readline())
print("Enter the annual interest (r%):")
r=parse(Float64,readline())
amount=p
max_amount=2p
for year in 1:10
amount+=amount*(r/100)
println("Year $year: $amount")
if amount > max_amount
println("Maximum limit reached !")
break
end
end
end
