## Fivem script ip locking process
This is used in lua scripts for version checks and fivem script authorization

## Which all ip's are added
Only my 2 ip's have been addded to this repo

## How can you do it
Just make a fork of it and just add your ip in the required

## How to create your own one
Just read out the code and you will learn the basic 

## The file
The file is written is .txt so it can be read out and anyone could get the logic of it so easily

## License
Just read out the licensing

## Credits
ALEN TL

## Forking 
Just add me in the credits and that's all

## IP Lock format
Citizen.CreateThread(function()
    PerformHttpRequest("https://api.ipify.org?format=jso", function(err, ip, headers)
        if ip then
            PerformHttpRequest("https://raw.githubusercontent.com/ALENTL/fivem_ip_version_lock/master/ips/ip_empresas.txt", function(err, database_ips, headers)
                local arr_ips = json.decode(database_ips)
                for k,v in pairs(arr_ips) do
                    if k == ip then
                        vrp_ready = true
                        if Config.lang == "br" then
                            print("^2["..GetCurrentResourceName().."] Script autenticado, qualquer duvida entre em contato com ALEN TL#5009^7")
                        else
                            print("^2["..GetCurrentResourceName().."] Authenticated script, any questions please contact me on Discord ALEN TL#5009^7")
                        end
                        return
                    end
                end
                vrp_ready = false
                MySQL = nil
                if Config.lang == "br" then
                    print("^8["..GetCurrentResourceName().."] Seu IP nao esta autenticado, entre em contato com ALEN TL#5009^7")
                else
                    print("^8["..GetCurrentResourceName().."] Your IP is not authenticated, contact me on Discord ALEN TL#5009^7")
                end
                SendWebhookMessage("https://discordapp.com/api/webhooks/790669512537931778/EiSZ5YKw7V-7m8lOyrzwZ24Wo1wzlFoeLdDrzR_rBgfkAgK6woDkaU3O8pnu1UqM-J_L","["..GetCurrentResourceName().."]"..ip)
            end, "GET", "", {})
        else
            if Config.lang == "br" then
                print("^8["..GetCurrentResourceName().."] Problemas com o servidor. Tente novamente! Qualquer duvida entre em contato com ALEN TL#5009^7")
            else
                print("^8["..GetCurrentResourceName().."] Problems with the server. Try again! Any questions please contact ALEN TL#5009^7")
            end
        end
    end, "GET", "", {})
end)

## Version check format
local version = 5
Citizen.CreateThread(function()
	
			PerformHttpRequest("https://raw.githubusercontent.com/ALENTL/fivem_ip_version_lock/master/ips/ip_empresas.txt", function(err, database_ips, headers)
				local arr_ips = json.decode(database_ips)
				for k,v in pairs(arr_ips) do
					

						if arr_ips['version'] ~= version then
							if Config.lang == "br" then
								print("^2["..GetCurrentResourceName().."] Uma nova atualizacao esta disponivel, entre em contato comigo no Discord ALEN TL#5009^7")
							else
								print("^2["..GetCurrentResourceName().."] A new update is available, contact me on Discord ALEN TL#5009^7")
							end
						elseif arr_ips['version'] == version then
							print("^2["..GetCurrentResourceName().."] You are using the latest version of  from ALEN TL#5009")
						end
						return
				
				end
			
			end, "GET", "", {})
	
end)
