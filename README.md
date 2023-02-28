# Cheetos Promotion Code Breaker

<center><img src = "https://upload.wikimedia.org/wikipedia/commons/thumb/2/24/Cheetos_logo.svg/2560px-Cheetos_logo.svg.png"></center>

## About the Promotion

In 2020, Cheetos launched a promotional campaign featuring Pac-Man-themed tazos. The promotion was part of a larger marketing campaign by the brand, which aimed to appeal to nostalgia and capture the attention of younger consumers.

The tazos were available in packs of Cheetos snacks, and each pack came with one Pac-Man tazo. There were a total of six different tazos to collect, featuring different characters and elements from the classic Pac-Man video game.

To promote the campaign, Cheetos created a TV commercial that featured animated versions of the Pac-Man characters. The ad showed the characters playing a game of Tazo Mania, the classic game that was popularized by the original tazo craze of the 1990s.

The Pac-Man tazo promotion was well-received by fans of the classic video game, as well as by those who had fond memories of collecting tazos in their youth. The promotion was a successful way for Cheetos to tap into the nostalgia trend and connect with consumers on a more emotional level.****

## About the Code

In order to generate the code associeted with the Tazo you can use the follow script

```ruby
def generate_code(number)
    charset = Array('A'..'Z') + Array('a'..'z')
    Array.new(number) {charset.sample}.join
end
string2 = generate_code(11)
puts string2.upcase  

number_s = rand(1..5).to_s
string = (0...4).map { (65 + rand(26)).chr + number_s}.join

puts string
#puts "Tamanho da String:  #{string.length}"
#string.each_byte {|c| puts c}

```

You can also generate multiple codes and save in the database.
```ruby
require 'pg'
ale_number = rand(0..9)
cont = 0
con = nil
#def generate_code(number)
  #ale_number = rand(0..10)
  #charset = Array('A'..'Z') + Array('a'..'z')
  #Array.new(number) { charset.sample }.join
#end

def generate_cod(number)
    charset = Array('A'..'Z') + Array('a'..'z') + Array(1..10)
	string = Array.new(number) {charset.sample}.join
	if string.length > 11
		nil
	else
		begin

		con = PG.connect :dbname => 'postgres', :user => 'postgres'
		puts con.server_version
		#con.exec "DROP TABLE IF EXISTS code_num"
		#con.exec "CREATE TABLE code_num(Code_Num varchar(20))"
		#con.exec "INSERT INTO code_num VALUES('#{string}')"
		t_msg = []
		#code = con.exec 'SELECT * FROM code_num'
		puts string
		rescue PG::Error => e

			puts e.message 
    
		ensure

			con.close if con
    
		end
		
	end
end

generate_cod(11)
#testio = (1..10).each {generate_cod(11)}

#number_test = 5

begin

    
	#testio2 = generate_cod(11)
	
	#Drop Database
	#con.exec "DROP TABLE IF EXISTS CODE_NUM"
	#Create database
	#con.exec "CREATE TABLE Code_Num(code_num INT)"
	#con.exec "INSERT INTO Code_Num VALUES(#{testio2})"
	

rescue PG::Error => e

    puts e.message 
    
ensure

    con.close if con
    
end

#charset.each do |number|
#end

#numbers = [1, 2, 3, 4, 5]
#sum = 0
#numbers.each do |number|
  #sum += number
#end

#sum = numbers.inject do |a, number|
   #a + number
#end

```

