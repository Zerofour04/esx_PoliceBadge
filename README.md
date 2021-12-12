# esx_policeBadge
PoliceBadge script made by xEnzoC94x. 
Enter in my Discord Channel: https://discord.gg/9YWr96c
or contact me in discord for any help: xEnzoC94x#0300

## Dependencies
 - esx_policejob 

## INSTALLATION
 - Download the repository
 - Extract it
 - Open client/main.lua in esx_policejob and Paste this code
 
 ----------------------------------------------------------------------------------------------------------------------------------------------------------------
 
 function openMenu()
  ESX.UI.Menu.Open(
	'default', GetCurrentResourceName(), 'id_card_menu',
	{
	    css = 'documenti',
		title    = 'Police Badge',
		elements = {
			{label = 'Check your ID', value = 'checkBadge'},
			{label = 'Show your ID', value = 'showBadge'},
		}
	},
	
	function(data, menu)
		local val = data.current.value

		
		if val == 'checkBadge' then
			TriggerServerEvent('policebadge:open', GetPlayerServerId(PlayerId()), GetPlayerServerId(PlayerId()))
                   local lPed = GetPlayerPed(-1)         
		else
			local player, distance = ESX.Game.GetClosestPlayer()
			
			if distance ~= -1 and distance <= 3.0 then
				if val == 'showBadge' then
				TriggerServerEvent('policebadge:open', GetPlayerServerId(PlayerId()), GetPlayerServerId(player))

				end
			else
			  ESX.ShowNotification('No players nearby')
			end
		
		end
	end,
	function(data, menu)
		menu.close()
	end
)
end
 
 CreateThread(function()
    while true do 
        Citizen.Wait(0)
		if IsControlJustReleased(0, 161) and not isDead and ESX.PlayerData.job and ESX.PlayerData.job.name == 'police' and not ESX.UI.Menu.IsOpen('default', GetCurrentResourceName(), 'id_card_menu') then
			openMenu()
		end
	end
end)
		
CreateThread(function()
    while true do 
        Citizen.Wait(5000)
			if ESX.PlayerData.job and ESX.PlayerData.job.name == 'police' then
            TriggerServerEvent('policebadge:ItemsBadge', GetPlayerPed(-1))
		end	
    end
end)



----------------------------------------------------------------------------------------------------------------------------------------------------------------

 - Paste esx_policeBadge 
 - Insert SQL files into your database
 - Add ```start esx_policeBadge``` to your server.cfg



If you want other script and you found any bugs you can join our discord to help you.
Whatever if you bought it or it's leaked I will help.

Enter in my Discord Channel: https://discord.gg/RxuxXAw
