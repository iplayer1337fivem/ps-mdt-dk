Dette er udelukkende et CSS edit og oversat til dansk.
Alt kodning og det fantastiske arbejde er generet af project sloth.
Denne udgave er mindre blå og mere sort, og så den danskificeret. Håber du kan lide det <3

#  ######  #          #    #     # ####### ######    #    #####   #####  ####### 
  #     # #         # #    #   #  #       #     #  ##   #     # #     # #    #  
# #     # #        #   #    # #   #       #     # # #         #       #     #   
# ######  #       #     #    #    #####   ######    #    #####   #####     #    
# #       #       #######    #    #       #   #     #         #       #   #     
# #       #       #     #    #    #       #    #    #   #     # #     #   #     
# #       ####### #     #    #    ####### #     # #####  #####   #####    #     
                                                                                

//ox_inventory>modules>shops>server.lua ca. linje 270//

local message = locale('purchased_for', count, fromItem.label, (currency == 'money' and locale('$') or     math.groupdigits(price)), (currency == 'money' and math.groupdigits(price) or ' '..Items(currency).label))
if string.find(fromData.name, "WEAPON_") then --Tilføjet pga PS MDT
local serial = metadata.serial--Tilføjet pga PS MDT
local imageurl = ("https://cfx-nui-ox_inventory/web/images/%s.png"):format(fromData.name)--Tilføjet pga PS MDT
local notes = "Købt i butik"--Tilføjet pga PS MDT
local owner = playerInv.owner--Tilføjet pga PS MDT
local weapClass = "Class"--Tilføjet pga PS MDT
local weapModel = fromData.name--Tilføjet pga PS MDT
			
AddWeaponToMDT(serial, imageurl, notes, owner, weapClass, weapModel)
end

//-- 


//indsæt dette i bunden ca linje 298 //

function AddWeaponToMDT(serial, imageurl, notes, owner, weapClass, weapModel)
    Citizen.CreateThread(function()
        Wait(500)

        local success, result = pcall(function()
            return exports['ps-mdt']:CreateWeaponInfo(serial, imageurl, notes, owner, weapClass, weapModel)
        end)

        if not success then
            print("Unable to add weapon to MDT")
        end
    end)
end

//
