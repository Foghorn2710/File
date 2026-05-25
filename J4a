begin
function gcd(a,b)
r=a%b
if r==0
return b
end
a=b
b=r
c=gcd(a,b)
return c
end
function lcm(a,b)
return ((a*b)/gcd(a,b))
end
println("Enter value of a:")
a=parse(Int64,readline())
println("Enter value of b:")
b=parse(Int64,readline())
println("GCD of $a and $b is:",gcd(a,b))
println("LCM of $a and $b is:",lcm(a,b))
end
