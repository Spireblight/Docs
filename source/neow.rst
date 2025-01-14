Interpreting the Neow bonus
===========================

.. module:: gamedata
    :no-index:

.. class:: NeowBonus

    This class handles everything to do with the Neow bonus. Some of the run-specific data will only be available if RunHistoryPlus is installed when the run is first started. In the absence of the mod, a sane default will be returned.

    This supports the base game bonuses as well as the MoreNeow mod.

    .. attribute:: all_bonuses

        A mapping of each bonus key the game stores to their description.

        :type: dict[str, str]

    .. attribute:: all_costs

        A mapping of each cost key the game stores to their description.

        :type: dict[str, str]

    .. attribute:: parser

        The parser instance that holds the run data to interpret. 

        :type: :class:`FileParser``

    .. property:: mod_data

        The internal mapping of the Neow bonus the game saves. Not intended for public use.

        :type: dict[str, Any]

    .. property:: choice_made

        Whether or not a choice was made for the Neow bonus.

        :type: bool

    .. property:: picked

        Human-readable version of the bonus picked.

        :type: str

    .. property:: skipped

        Human-readable version of the bonuses that were skipped.

        :type: Generator[str]

    .. method:: as_str()

        Returns a full message of the picked and skipped choices.

    .. property:: has_info

        Whether there is data about the Neow bonus.

        :type: bool

    .. property:: has_data

        Whether there is full data (with the RunHistoryPlus mod) to be able to give the most reliable information.

        :type: bool

    .. property:: current_hp

        Gives the current HP of the run before entering floor 1. This is not guaranteed to be accurate if character mods are involved. This and other similar properties are included so that the signature would match that of :class:`NodeData` instances. This is relevant for statistic aggregation (e.g. graphs) that uses floor 0 (the Neow bonus) as part of the data set.

        :type: int

    .. property:: max_hp

        Gives the max HP of the run before entering floor 1. This is not guaranteed to be accurate if character mods are involved. This and other similar properties are included so that the signature would match that of :class:`NodeData` instances. This is relevant for statistic aggregation (e.g. graphs) that uses floor 0 (the Neow bonus) as part of the data set.

        :type: int

    .. property:: gold

        Gives the gold of the run before entering floor 1. This is not guaranteed to be accurate if character mods are involved. This and other similar properties are included so that the signature would match that of :class:`NodeData` instances. This is relevant for statistic aggregation (e.g. graphs) that uses floor 0 (the Neow bonus) as part of the data set.

        :type: int

    .. property:: floor

        Returns the floor number. This is always zero. This and other similar properties are included so that the signature would match that of :class:`NodeData` instances. This is relevant for statistic aggregation (e.g. graphs) that uses floor 0 (the Neow bonus) as part of the data set.

        :type: int

    .. property:: floor_time

        Returns the time spent in the floor. Unless RunHistoryPlus is updated to include time spent on floor 0, this will always be inaccurate and return zero. This and other similar properties are included so that the signature would match that of :class:`NodeData` instances. This is relevant for statistic aggregation (e.g. graphs) that uses floor 0 (the Neow bonus) as part of the data set.

        :type: int

    .. property:: cards_obtained

        Returns a list of cards obtained from Neow, if any. Each string is the internal name to provide to :class:`CardData`. If the RunHistoryPlus mod is not installed, this will always be an empty list.

        :type: list[str]

    .. property:: cards_removed

        Returns a list of cards removed by Neow, if any. Each string is the internal name to provide to :class:`CardData`. If the RunHistoryPlus mod is not installed, this will always be an empty list.

        :type: list[str]

    .. property:: cards_transformed

        Returns a list of cards transformed by Neow, if any. These are the cards that were removed by a transformation. The cards received from the transformation will be in :attr:`cards_obtained`. Each string is the internal name to provide to :class:`CardData`. If the RunHistoryPlus mod is not installed, this will always be an empty list.

        :type: list[str]

    .. property:: cards_upgraded

        Returns a list of cards upgraded by Neow, if any. Each string is the internal name to provide to :class:`CardData`. If the RunHistoryPlus mod is not installed, this will always be an empty list.

        :type: list[str]

    .. method:: get_hp()

        Calculates the current and max HP of the character with the ascension level, the max HP lost or gained, and the damage taken. This uses hardcoded values and does not support modded characters. This may change. Other code should use the :attr:`current_hp` and :attr:`max_hp` properties instead of this.

        :rtype: tuple[int, int]

    .. method:: get_gold()

        Calculates the current gold of the character with gold gained or lost, or the Old Coin. If the character does not start with 99 gold, this resuld will be inaccurate. Other code should use the :attr:`gold` property instead of this.

        :rtype: int

    .. method:: get_cards()

        Returns the state of the deck entering the first floor. This includes the starter cards and any cards that were obtained, and does not include cards that were removed or transformed away. This does not currently support modded characters. External code should use the :attr:`cards` property instead.

        :rtype: list[str]
        :return: A list of cards, to be passed to :class:`CardData`
        :raise: ValueError on unsupported characters

    .. property:: cards

        A list of all cards in the deck entering floor 1. This is included to keep track of the deck across floors. Or it will be, once I do it.

        :type: list[:class:`CardData`]

    .. method:: card_delta()

        Calculates the difference in card count between entering and exiting the node.

        :type: int

    .. method:: relic_delta()

        Calculates the difference in relic count between entering and exiting the node.

        :type: int

    .. method:: potion_delta()

        Calculates the difference in potion count between entering and exiting the node.

        :type: int

    .. method:: fights_delta()

        Calculates the difference in fight count between entering and exiting the node.

        :type: int

    .. method:: turns_delta()

        Calculates the difference in turn count between entering and exiting the node.

        :type: int

    .. property:: card_count

        Total card count in the deck at this point in the run, at the end of the node.

        :type: int

    .. property:: relic_count

        Total relic count at this point in the run, at the end of the node.

        :type: int

    .. property:: potion_count

        Total potion count at this point in the run, at the end of the node.

        :type: int

    .. property:: fights_count

        Total fight count at this point in the run, at the end of the node.

        :type: int

    .. property:: turns_count

        Total turn count at this point in the run, at the end of the node.

        :type: int
