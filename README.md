last-line-of-defence-untested-unchecked
=======================================
-- The Last Line Of Defense
-- start event gossip

UPDATE `creature_template` SET `gossip_menu_id`=30657 WHERE `entry`=30657;
DELETE FROM `gossip_menu` WHERE `entry`=30657;
INSERT INTO `gossip_menu` (`entry`, `text_id`) VALUES (30657, 1);
DELETE FROM `gossip_menu_option` WHERE `menu_id`=30657;
INSERT INTO `gossip_menu_option` (`menu_id`, `id`, `option_icon`, `option_text`, `option_id`, `npc_option_npcflag`, `action_menu_id`, `action_poi_id`, `action_script_id`, `box_coded`, `box_money`, `box_text`) VALUES
('30657', '0', '0', 'The Lich kings minnions are comming. May i prepare cannon for you?', '1', '3', '0', '0', '0', '0', '0', 'Are you ready to defend the camp?');
/*
+DELETE FROM `gossip_scripts` WHERE `id`=30657;
+INSERT INTO `gossip_scripts` (`id`, `delay`, `command`, `datalong`, `datalong2`, `dataint`, `x`, `y`, `z`, `o`) VALUES
+(30657, 0, 10, 730017, 600000, 0, 6291.32, 140.507, 386.517, 4.43048),
+(30657, 0, 10, 730017, 600000, 0, 6311.92, 127.115, 389.501, 3.98517),
+(30657, 0, 10, 730019, 600000, 0, 6325.59, 115.692, 390.431, 3.78489),
+(30657, 0, 10, 730019, 600000, 0, 6343.48, 94.1783, 391.444, 3.54927),
+(30657, 0, 10, 730019, 600000, 0, 6339.35, 67.395, 390.09, 2.6657),
+(30657, 0, 10, 730017, 600000, 0, 6265.25, 145.87, 383.394, 4.59306),
+(30657, 0, 10, 730021, 600000, 0, 6272.11, 77.81, 393.821, 0.69),
+(30657, 0, 6, 571, 0, 0, 6272.30, 77.69, 393.82, 0.82),
+(30657, 0, 10, 30236, 600000, 0, 6282.92, 70.2466, 396.427, 0.936193),
+(30657, 0, 10, 30236, 600000, 0, 6273.69, 79.3612, 396.309, 0.791233),
+(30657, 0, 10, 30236, 600000, 0, 6264.18, 85.28, 391.7, 0.68),
+(30657, 0, 10, 30236, 600000, 0, 6289.03, 61.45, 391.81, 0.92);
+*/
-- skript ke zkontrolovani
SET @NPC_Fezzik :=30657;
UPDATE `creature_template` SET `AIName`='SmartAI',`ScriptName`='',`npcflag`=3 WHERE `entry`=@NPC_Fezzik;
DELETE FROM `smart_scripts` WHERE `entryorguid`=@NPC_Fezzik AND `source_type`=0;
INSERT INTO `smart_scripts` (`entryorguid`,`source_type`,`id`,`link`,`event_ty pe`,`event_phase_mask`,`event_chance`,`event_flags `,`event_param1`,`event_param2`,`event_param3`,`ev ent_param4`,`action_type`,`action_param1`,`action_ param2`,`action_param3`,`action_param4`,`action_pa ram5`,`action_param6`,`target_type`,`target_param1 `,`target_param2`,`target_param3`,`target_x`,`targ et_y`,`target_z`,`target_o`,`comment`) VALUES
(@NPC_Fezzik,0,0,0,1,0,100,0,1000,1000,1000,1000,1 5,3070,0,0,0,0,0,18,1,0,0,0,0,0,0,'Complete quest on player range'),
(@NPC_Fezzik,0,1,2,62,0,100,0,30657,0,0,0,12,30236 ,3,600000,0,0,0,8,0,0,0,6282.92,70.2466,396.427,0. 936193,'Siegemaster Fezzik - summon cannon on gossip'),
(@NPC_Fezzik,0,2,3,61,0,100,0,0,0,0,0,12,30236,3,6 00000,0,0,0,8,0,0,0,6289.03,61.45,391.81,0.92,'Sie gemaster Fezzik - summon cannon on gossip'),
(@NPC_Fezzik,0,3,4,61,0,100,0,0,0,0,0,12,30236,3,6 00000,0,0,0,8,0,0,0,6273.69,79.3612,396.309,0.7912 33,'Siegemaster Fezzik - summon cannon on gossip'),
(@NPC_Fezzik,0,4,5,61,0,100,0,0,0,0,0,12,30236,3,6 00000,0,0,0,8,0,0,0,6264.18,85.28,391.7,0.68,'Sieg emaster Fezzik - summon cannon on gossip'),
(@NPC_Fezzik,0,5,6,61,0,100,0,0,0,0,0,12,730017,3, 600000,0,0,0,8,0,0,0,6291.32, 140.507, 386.517, 4.43048,'Siegemaster Fezzik - summon spawner on gossip'),
(@NPC_Fezzik,0,6,7,61,0,100,0,0,0,0,0,12,730017,3, 600000,0,0,0,8,0,0,0,6311.92, 127.115, 389.501, 3.98517,'Siegemaster Fezzik - summon spawner on gossip'),
(@NPC_Fezzik,0,7,8,61,0,100,0,0,0,0,0,12,730017,3, 600000,0,0,0,8,0,0,0,6265.25, 145.87, 383.394, 4.59306,'Siegemaster Fezzik - summon spawner on gossip'),
(@NPC_Fezzik,0,8,9,61,0,100,0,0,0,0,0,12,730019,3, 600000,0,0,0,8,0,0,0,6325.59, 115.692, 390.431, 3.78489,'Siegemaster Fezzik - summon spawner on gossip'),
(@NPC_Fezzik,0,9,10,61,0,100,0,0,0,0,0,12,730019,3 ,600000,0,0,0,8,0,0,0,6343.48, 94.1783, 391.444, 3.54927,'Siegemaster Fezzik - summon spawner on gossip'),
(@NPC_Fezzik,0,10,11,61,0,100,0,0,0,0,0,12,730019, 3,600000,0,0,0,8,0,0,0,6339.35, 67.395, 390.09, 2.6657,'Siegemaster Fezzik - summon spawner on gossip'),
(@NPC_Fezzik,0,11,12,61,0,100,0,0,0,0,0,81,2,0,0,0 ,0,0,7,0,0,0,0,0,0,0,'Fezzik - set flag to gossip'),
(@NPC_Fezzik,0,12,0,1,0,100,0,600000,600000,0,0,81 ,3,0,0,0,0,0,7,0,0,0,0,0,0,0,'Fezzik - set flag back to quest giver ');



-- Argent Cannon
SET @ENTRY := 30236;
SET @VEHICLE := 246;
-- spawn utocicich mobu
DELETE FROM `smart_scripts` WHERE `entryorguid`IN (730017, 730019, 30593);
INSERT INTO `smart_scripts` (`entryorguid`, `source_type`, `id`, `link`, `event_type`, `event_phase_mask`, `event_chance`, `event_flags`, `event_param1`, `event_param2`, `event_param3`, `event_param4`, `action_type`, `action_param1`, `action_param2`, `action_param3`, `action_param4`, `action_param5`, `action_param6`, `target_type`, `target_param1`, `target_param2`, `target_param3`, `target_x`, `target_y`, `target_z`, `target_o`, `comment`) VALUES
(730017, 0, 0, 0, 1, 0, 100, 0, 20000, 30000, 2000, 3000, 12, 30593, 3, 60000, 0, 0, 0, 1, 0, 0, 0, 0, 0, 0, 0, 'Summon spider'),
(730017, 0, 1, 0, 1, 0, 100, 0, 20000, 80000, 30000, 40000, 12, 30575, 3, 60000, 0, 0, 0, 1, 0, 0, 0, 0, 0, 0, 0, 'Summon wyrm'),
(730019, 0, 0, 0, 1, 0, 100, 0, 20000, 30000, 2000, 3000, 12, 730020, 3, 60000, 0, 0, 0, 1, 0, 0, 0, 0, 0, 0, 0, 'Summon spider'),
(730019, 0, 1, 0, 1, 0, 100, 0, 20000, 80000, 30000, 40000, 12, 30575, 3, 60000, 0, 0, 0, 1, 0, 0, 0, 0, 0, 0, 0, 'Summon wyrm'),
(730017, 0, 2, 0, 1, 0, 100, 0, 20000, 30000, 15000, 15000, 12, 30189, 3, 30000, 0, 0, 0, 1, 0, 0, 0, 6288.7, 96.6109, 390.21, 0.8, 'Summon defender'),
(730019, 0, 2, 0, 1, 0, 100, 0, 20000, 30000, 15000, 15000, 12, 30189, 3, 30000, 0, 0, 0, 1, 0, 0, 0, 6301.15, 86.1998, 389.705, 0.8, 'Summon defender');
UPDATE `quest_template` SET `StartScript`=13086 WHERE `Id`=13086;

/*
-- spawn dela a vyvolavace utoku
DELETE FROM `quest_start_scripts` WHERE `id`=13086;
INSERT INTO `quest_start_scripts` (`id`, `delay`, `command`, `datalong`, `datalong2`, `dataint`, `x`, `y`, `z`, `o`) VALUES
-(13086, 0, 10, 730017, 180000, 0, 6291.32, 140.507, 386.517, 4.43048),
-(13086, 0, 10, 730017, 180000, 0, 6311.92, 127.115, 389.501, 3.98517),
-(13086, 0, 10, 730019, 180000, 0, 6325.59, 115.692, 390.431, 3.78489),
-(13086, 0, 10, 730019, 180000, 0, 6343.48, 94.1783, 391.444, 3.54927),
-(13086, 0, 10, 730019, 180000, 0, 6339.35, 67.395, 390.09, 2.6657),
-(13086, 0, 10, 730017, 180000, 0, 6265.25, 145.87, 383.394, 4.59306),
-(13086, 0, 10, 730021, 180000, 0, 6272.11, 77.81, 393.821, 0.69),
+(13086, 0, 10, 730017, 600000, 0, 6291.32, 140.507, 386.517, 4.43048),
+(13086, 0, 10, 730017, 600000, 0, 6311.92, 127.115, 389.501, 3.98517),
+(13086, 0, 10, 730019, 600000, 0, 6325.59, 115.692, 390.431, 3.78489),
+(13086, 0, 10, 730019, 600000, 0, 6343.48, 94.1783, 391.444, 3.54927),
+(13086, 0, 10, 730019, 600000, 0, 6339.35, 67.395, 390.09, 2.6657),
+(13086, 0, 10, 730017, 600000, 0, 6265.25, 145.87, 383.394, 4.59306),
+(13086, 0, 10, 730021, 600000, 0, 6272.11, 77.81, 393.821, 0.69),
(13086, 0, 6, 571, 0, 0, 6272.30, 77.69, 393.82, 0.82),
-(13086, 0, 10, 30236, 180000, 0, 6282.92, 70.2466, 396.427, 0.936193),
-(13086, 0, 10, 30236, 180000, 0, 6273.69, 79.3612, 396.309, 0.791233);
+(13086, 0, 10, 30236, 600000, 0, 6282.92, 70.2466, 396.427, 0.936193),
+(13086, 0, 10, 30236, 600000, 0, 6273.69, 79.3612, 396.309, 0.791233),
+(13086, 0, 10, 30236, 600000, 0, 6264.18, 85.28, 391.7, 0.68),
+(13086, 0, 10, 30236, 600000, 0, 6289.03, 61.45, 391.81, 0.92);
+*/

-- nastaveni utocniku
UPDATE `creature_template` SET `minrangedmg`=1000,`maxrangedmg`=2000,`InhabitType `=4 WHERE `entry`=30575;

-- ------------------------------------------ --
-- quest "The Last Line Of Defense" 13086 fix --
-- ------------------------------------------ --

-- on retail players can use Argent Canons to pew-pew quest mobs,
-- since it's more like science-fiction for us, players are allowed to kill mobs by sword and fire.
-- NPC "Frostbrood Destroyer" 30575 needed for quest credit #2 added and spawned
UPDATE `creature_template`
SET
`faction_A` = '2068',
`faction_H` = '2068',
`minrangedmg` = '345',
`maxrangedmg` = '509',
`minlevel` = '80',
`maxlevel` = '80',
`armor` = '9729',
`mindmg` = '1170',
`maxdmg` = '3470',
`attackpower` = '342',
`dmg_multiplier` = '2',
`minhealth` = '315000',
`maxhealth` = '315000',
`InhabitType` = '3'
WHERE
`entry` = '30575';
DELETE FROM `creature` WHERE `id` = '30575';
INSERT INTO `creature` (id, map, position_x, position_y, position_z, orientation, spawntimesecs) VALUES
(30575, 571, 6335.826172, 82.110123, 409.224274, 3.138359, 300),
(30575, 571, 6457.640625, 171.508743, 409.985840, 2.494332, 300),
(30575, 571, 6319.731445, 212.167740, 391.011688, 4.739780, 300),
(30575, 571, 6034.281250, 63.817360, 394.400238, 0.973792, 300);
UPDATE `creature`
SET
`id` = '30575'
WHERE
`id` = '30674';

-- Argent Towers spawned for better look, but they don't work
DELETE FROM `creature` WHERE `id` = '30236';
INSERT INTO `creature` (id, map, position_x, position_y, position_z, orientation, spawntimesecs) VALUES
(30236, 571, 6296.888672, 53.354115, 404.575562, 0.782158, 900),
(30236, 571, 6255.935059, 92.995056, 404.473083, 1.567560
, 900),
(30236, 571, 6219.520508, 59.812351, 394.064758, 1.944548
, 900),
(30236, 571, 6162.470215, 60.321831, 394.067474, 2.089845, 900);
-- since for quest credit #1 can be killed difrent mobs, script is the best solution for counting frags
DELETE FROM `creature_ai_scripts` WHERE `creature_id` IN ('30204', '30333', '30205', '30206', '30673', '31043');
INSERT INTO `creature_ai_scripts` (creature_id, event_type, event_chance, action1_type, action1_param1, action1_param2, comment) VALUES
(30204, 6, 100, 33, 30670, 6, "Gives quest 13086 credit"),
(30333, 6, 100, 33, 30670, 6, "Gives quest 13086 credit"),
(30205, 6, 100, 33, 30670, 6, "Gives quest 13086 credit"),
(30206, 6, 100, 33, 30670, 6, "Gives quest 13086 credit"),
(30673, 6, 100, 33, 30670, 6, "Gives quest 13086 credit"),
(31043, 6, 100, 33, 30670, 6, "Gives quest 13086 credit");

last line of defence, quest for icecrown.