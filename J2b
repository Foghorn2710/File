function computer_pay()
print("Enter number of hours:")
hours = parse(Int,readline())
print("Rate of pay:")
rate= parse(Int,readline())
if hours <= 40
regularpay = hours*rate
overtimepay= 0
elseif hours > 40
regularpay = 40*rate
overtimepay = (hours-40)*rate*1.5
end
grosspay = regularpay + overtimepay
println("Regularpay = $regularpay, Overtimepay = $overtimepay, Grosspay = $grosspay")
end


computer_pay()
