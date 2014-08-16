Plugin
======
package me.ryguyl21.bossbar;

import java.util.ArrayList;
import java.util.List;
import java.util.Random;

import me.confuser.barapi.BarAPI;

import org.bukkit.entity.Player;
import org.bukkit.event.EventHandler;
import org.bukkit.event.Listener;
import org.bukkit.event.player.PlayerJoinEvent;
import org.bukkit.plugin.java.JavaPlugin;

public class Tutorial extends JavaPlugin implements Listener  {
	
	public void onEnable() {
        getServer().getPluginManager().registerEvents(this, this);
    }
   
    @EventHandler
    public void onJoin(PlayerJoinEvent e){
        Player p = e.getPlayer();
        // BarAPI.setMessage(p, "Ryguyl21 Bossbar test");
        showBarChanging(p);
    }
   
    public void showBarChanging(final Player p){
        getServer().getScheduler().scheduleSyncRepeatingTask(this, new Runnable(){
            public void run(){
                Random random = new Random();
                List<String> list = new ArrayList<>();
                // Use § to add color codes!
                list.add("Message 1");
                list.add("Message 2");
                list.add("Message 3");
                list.add("Message 4");
                list.add("Message 5");
                list.add("Message 6");
                list.add("Message 7");
                list.add("Message 8");
                list.add("Message 9");
                list.add("Message 10");
                String message = (String) list.get(random.nextInt(list.size()));
                BarAPI.setMessage(p, message);
            }
           
        }, 0L, 1 * 50); // To change the time it takes to change messages change the amount of ticks (currently set to 50)
    }
 
}
