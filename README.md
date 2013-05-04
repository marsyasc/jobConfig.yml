# Jobs configuration.
#
# Stores information about each job.
#
# NOTE: When having multiple jobs, both jobs will give the income payout to the player
# even if they give the pay for one action (make the configurations with this in mind)
# and each job will get the respective experience.
#
# e.g If player has 2 jobs where job1 gives 10 income and experience for killing a player 
# and job2 gives 5 income and experience for killing a player. When the user kills a player
# they will get 15 income and job1 will gain 10 experience and job2 will gain 5 experience.

Jobs:
  # must be one word
  Woodcutter:
    # full name of the job (displayed when browsing a job, used when joining and leaving)
    # also can be used as a prefix for the user's name if the option is enabled.
    # Shown as a prefix only when the user has 1 job.
    #
    # NOTE: Must be 1 word
    fullname: Woodcutter
    # Shortened version of the name of the job. Used as a prefix when the user has more 
    # than 1 job
    shortname: W
    description: Earns money felling and planting trees  
    # The colour of the name, for a full list of supported colours, go to the message config.
    ChatColour: GREEN
    # Option to let you choose what kind of prefix this job adds to your name.
    # options are: full, title, job, shortfull, shorttitle, shortjob and none
    chat-display: full
    # [OPTIONAL] - the maximum level of this class
    #max-level: 10
    # [OPTIONAL] - the maximum number of users on the server that can have this job at 
    # any one time (includes offline players).
    #slots: 1
    # Equation used for calculating how much experience is needed to go to the next level.
    # Available parameters:
    #   numjobs - the number of jobs the player has
    #   joblevel - the level the player has attained in the job.
    # NOTE: Please take care of the brackets when modifying this equation.
    leveling-progression-equation: 100*((1.13+(0.01*(numjobs-1)))^(joblevel-1))
    # Equation used for calculating how much income is given per action for the job level.
    # Available parameters:
    #   baseincome - the income for the action at level 1 (as set in the configuration).
    #   joblevel - the level the player has attained in the job.
    # NOTE: Please take care of the brackets when modifying this equation.
    income-progression-equation: baseincome*((1.05)^(joblevel-1))
     # Equation used for calculating how much experience is given per action for the job level.
    # Available parameters:
    #   baseexperience - the experience for the action at level 1 (as set in the configuration).
    #   joblevel - the level the player has attained in the job.
    # NOTE: Please take care of the brackets when modifying this equation.
    experience-progression-equation: baseexperience*((1.05)^(joblevel-1))
    ########################################################################
    # Section used to configure what items the job gets paid for, how much
    # they get paid and how much experience they gain.
    #
    # For break and place, the block name or id is used.
    # You can select a sub-type by using a '-' between the id and the bit
    # value for the sub-type. e.g LOG-0 = usual log, LOG-2 = birch log
    # 17-2 = birch log.
    #
    # If no sub-type is give, the payout will be for all sub-types.
    #
    # To get a list of all available block types, check the
    # bukkit JavaDocs for a complete list of block types
    # http://jd.bukkit.org/apidocs/org/bukkit/Material.html
    # 
    # For kill tags (Kill and custom-kill), the name is the name of the
    # mob.
    # Available mobs:
    #   Chicken
    #   Cow
    #   Pig
    #   Sheep
    #   Wolf
    #   Creeper
    #   Giant
    #   Skeleton
    #   Spider
    #   Zombie
    #   PigZombie
    #   Squid
    #   Ghast
    #   Player
    #   Slime
    #
    # NOTE: mob names are case sensitive.
    #
    # For custom-kill, it is the name of the job (also case sensitive).
    # 
    # NOTE: If a job has both the pay for killing a player and for killing a
    # specific class, they will get both payments.
    ########################################################################
    # payment for breaking a block
    Break:
      # block name/id (with optional sub-type)
      LOG:
        # base income
        income: 5.0
        # base experience
        experience: 5.0
    # payment for placing a block
      WOOD: 
        income: 2.0
        experience: 2.0
    # killing a mob
    Kill:
      # mob name
      Player:
        # base income
        income: 7.5
        # base experience
        experience: 7.5
    # killing a jobs class
    custom-kill:
      # full name of the jobs class
      Woodcutter:
        # base income
        income: 10.0
        # base experience
        experience: 10.0
    # permissions granted for joining class
    permissions:
      # example node
      aaaaaatest.node:
        # true to give, false to revoke
        value: true
        # minimum level needed to grant permission.  Use 0 for all levels
        level: 0
      aaaaaatest.node2:
        value: true
        # Permission granted when reaching level 10
        level: 10
  Miner:
    fullname: Miner
    shortname: M
    description: Earns money mining minerals and ores.
    ChatColour: DARK_GRAY
    chat-display: full
    #max-level: 10
    #slots: 10
    leveling-progression-equation: 100*((1.13+(0.01*(numjobs-1)))^(joblevel-1))
    income-progression-equation: baseincome*((1.05)^(joblevel-1))
    experience-progression-equation: baseexperience*((1.05)^(joblevel-1))
    Break:
      STONE:
        income: 2.0
        experience: 2.0
      COAL_ORE:
        income: 3.0
        experience: 3.0
      GLOWING_REDSTONE_ORE:
        income: 3.0
        experience: 3.0
      IRON_ORE: 
        income: 3.50
        experience: 3.50
      GOLD_ORE:
        income: 3.0
        experience: 3.0
      LAPIS_ORE:
        income: 3.0
        experience: 3.0
      DIAMOND_ORE:
        income: 5.0
        experience: 5.0
      OBSIDIAN: 
        income: 3.5
        experience: 3.5
      MOSSY_COBBLESTONE:
        income: 2.0
        experience: 2.0
    Kill:
      Player:
        income: 7.5
        experience: 7.5
    custom-kill:
      Miner:
        income: 10.0
        experience: 10.0
  Builder:
    fullname: Builder
    shortname: B
    description: Earns money for building structures.
    ChatColour: WHITE
    chat-display: full
    #max-level: 10
    #slots: 10
    leveling-progression-equation: 100*((1.13+(0.01*(numjobs-1)))^(joblevel-1))
    income-progression-equation: baseincome*((1.05)^(joblevel-1))
    experience-progression-equation: baseexperience*((1.05)^(joblevel-1))
    Place:
      COBBLESTONE:
        income: 1.0
        experience: 1.0
      WOOD:
        income: 1.5
        experience: 1.5
      FENCE:
        income: 1.5
        experience: 1.5
      WOOL:
        income: 1.5
        experience: 1.5
      STONE:
        income: 2.25
        experience: 2.25
      GLOWSTONE:
        income: 3.0
        experience: 3.0
      SANDSTONE:
        income: 2.0
        experience: 2.0
      GLASS:
        income: 3.0
        experience: 3.0
      BRICK:
        income: 4.0
        experience: 4.0
      LAPIS_BLOCK:
        income: 5.0
        experience: 5.0
      DOUBLE_STEP:
        income: 2.0
        experience: 2.0
      STEP:
        income: 2.0
        experience: 2.0
      BOOKSHELF:
        income: 3.0
        experience: 3.0
      WOOD_STAIRS:
        income: 2.0
        experience: 2.0
      COBBLESTONE_STAIRS:
        income: 2.0
        experience: 2.0
      MOSSY_COBBLESTONE:
        income: 5.0
        experience: 5.0
      DIAMOND_BLOCK:
        income: 5.0
        experience: 5.0
      GOLD_BLOCK:
        income: 5.0
        experience: 5.0
    Kill:
      Player:
        income: 7.5
        experience: 7.5
    custom-kill:
      Builder:
        income: 10.0
        experience: 10.0
  Digger:
    fullname: Digger
    shortname: D
    description: Earns money for terraforming the world.
    ChatColour: GOLD
    chat-display: full
    #max-level: 10
    #slots: 10
    leveling-progression-equation: 100*((1.13+(0.01*(numjobs-1)))^(joblevel-1))
    income-progression-equation: baseincome*((1.05)^(joblevel-1))
    experience-progression-equation: baseexperience*((1.05)^(joblevel-1))
    Break:
      DIRT:
        income: 2.0
        experience: 2.0
      GRASS:
        income: 2.0
        experience: 2.0
      GRAVEL:
        income: 2.0
        experience: 2.0
      SAND:
        income: 2.0
        experience: 2.0
      CLAY:
        income: 2.0
        experience: 2.0
    Kill:
      Player:
        income: 7.5
        experience: 7.5
    custom-kill:
      Digger:
        income: 10.0
        experience: 10.0
  Hunter:
    fullname: Hunter
    shortname: H
    description: Earns money killing animals and monsters.
    ChatColour: RED
    chat-display: full
    #max-level: 10
    #slots: 10
    leveling-progression-equation: 100*((1.13+(0.01*(numjobs-1)))^(joblevel-1))
    income-progression-equation: baseincome*((1.05)^(joblevel-1))
    experience-progression-equation: baseexperience*((1.05)^(joblevel-1))
    Kill:
      Chicken:
        income: 2.5
        experience: 2.5
      Cow:
        income: 2.5
        experience: 2.5
      Pig:
        income: 2.5
        experience: 2.5
      Sheep: 
        income: 2.5
        experience: 2.5
      Wolf: 
        income: 2.50
        experience: 2.50
      Creeper: 
        income: 5.0
        experience: 5.0
      Skeleton: 
        income: 5.0
        experience: 5.0
      Spider:
        income: 5.0
        experience: 5.0
      Zombie: 
        income: 5.0
        experience: 5.0
      Player:
        income: 7.5
        experience: 7.5
    custom-kill:
      Woodcutter:
        income: 10.0
        experience: 10.0
      Miner:
        income: 10.0
        experience: 10.0
      Digger:
        income: 10.0
        experience: 10.0
      Farmer:
        income: 10.0
        experience: 10.0
      Builder:
        income: 10.0
        experience: 10.0
      Hunter:
        income: 10.0
        experience: 10.0
  Fisherman:
    fullname: Fisherman
    shortname: Fi
    description: Earns money from fishing.
    ChatColour: AQUA
    chat-display: full
    #max-level: 10
    #slots: 10
    leveling-progression-equation: 100*((1.13+(0.01*(numjobs-1)))^(joblevel-1))
    income-progression-equation: baseincome*((1.05)^(joblevel-1))
    experience-progression-equation: baseexperience*((1.05)^(joblevel-1))
    Fish:
      RAW_FISH:
        income: 4.0
        experience: 4.0
    Kill:
      Player:
        income: 7.5
        experience: 7.5
    custom-kill:
      Fisherman:
        income: 10.0
        experience: 10.0
  None:
    fullname: None
    shortname: N
    ChatColour: WHITE
    chat-display: none
    #max-level: 10
    #slots: 10
    leveling-progression-equation: 100*((1.13+(0.01*(numjobs-1)))^(joblevel-1))
    income-progression-equation: baseincome*((1.05)^(joblevel-1))
    experience-progression-equation: baseexperience*((1.05)^(joblevel-1))
    Kill:
      Player:
        income: 7.5
