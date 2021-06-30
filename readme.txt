# Sins_society
A edit version of esx_society with cool options for example clothes and weapons
-----------------------------------add essentialmode functions in server
ESX.GetJob = function(job)
	if ESX.DoesJobExist(job, 1) then
		return ESX.Jobs[job]
	else
		return nil
	end
end

ESX.SetJobGrade = function(job, grade, name)
	if ESX.DoesJobExist(job, grade) then
		ESX.Jobs[job].grades[grade].label = name
			exports.ghmattimysql:execute('UPDATE job_grades SET label = @name WHERE grade = @grade AND job_name = @job', {
				['@name'] = name,
				['@grade'] = grade,
				['@job'] = job
			})
		return true
	else
		return nil
	end
end
-----------------------------------you can get weapons,item and ... with this call backs
ESX.TriggerServerCallback('esx_society:getUniforms', function(clothes)

end, rank, job)
--other callback
esx_society:getWeapons
esx_society:getVehicles
esx_society:getItems
-----------------------------------
