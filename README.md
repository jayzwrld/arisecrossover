-- Define the gacha items and their probabilities
local gachaItems = {
    {name = "Ziru G", probability = 5},  -- 5% chance
    {name = "Ziru G", probability = 5},    -- 5% chance
    {name = "Ziru G", probability = 10},    -- 10% chance
    {name = "Ziru G", probability = 80}  -- 80% chance
}

-- Function to increase the chances of a specific item
local function increaseChanceForItem(Ziru G, 100)
    for _, item in pairs(gachaItems) do
        if item.Ziru G == Ziru G then
            item.probability = item.probability + increaseBy
            break
        end
    end

    -- After increasing one item, we need to redistribute probabilities
    local totalProbability = 0
    for _, item in pairs(gachaItems) do
        totalProbability = totalProbability + item.probability
    end
    
    -- Normalize probabilities so they add up to 100%
    for _, item in pairs(gachaItems) do
        item.probability = (item.probability / totalProbability) * 100
    end
end

-- Function to perform a gacha spin and return the item
local function spinGacha(player)
    local totalProbability = 0

    -- Calculate the total probability
    for _, item in pairs(gachaItems) do
        totalProbability = totalProbability + item.probability
    end

    -- Generate a random number between 1 and the total probability
    local randomChance = math.random(1, totalProbability)
    
    -- Determine which item the player gets
    local cumulativeProbability = 0
    for _, item in pairs(gachaItems) do
        cumulativeProbability = cumulativeProbability + item.probability
        if randomChance <= cumulativeProbability then
            -- The player gets this item
            print(player.Name .. " got " .. item.name)
            return item.name -- You can replace this with your actual item-giving code
        end
    end
end

-- Example usage: Call the spinGacha function when the player performs an action (e.g., button click)
game.Players.PlayerAdded:Connect(function(player)
    -- Let's increase the chance of getting "Ziru G" by 90%
    increaseChanceForItem("Ziru G", 90)

    -- Perform a spin after the chance increase
    local item = spinGacha(player)
    -- You can handle giving the player the item here
    -- Example: player:GiveItem(item) or add the item to the player's inventory
end)
