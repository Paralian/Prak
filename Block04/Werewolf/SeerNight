package phases;

import java.util.ArrayList;
import java.util.List;

import game.Poll;
import phases.result.PhaseResult;
import phases.result.PlayerRevealedResult;
import roles.*;

public class SeerNight extends Phase {
    
    public SeerNight(List<Player> players) {
        super(players);
    }
    
    /* (non-Javadoc)
     * @see phases.Phase#preparePlayers(java.util.List)
     */
    @Override
    protected void preparePlayers(List<Player> players) {
        for (Player numberOfPlayer : players) {
            if (numberOfPlayer.getStatus() != Player.PlayerStatus.DEAD) {
                if (players instanceof Seer) {
                    numberOfPlayer.setStatus(Player.PlayerStatus.AWAKE);
                } else {
                    numberOfPlayer.setStatus(Player.PlayerStatus.ASLEEP);
                }
            }
        }
    }
    
    /* (non-Javadoc)
     * @see phases.Phase#concludePhase()
     */
    @Override
    public PhaseResult concludePhase() {
        Seer.PlayerAlignment seeMe = Seer.PlayerAlignment.UNKNOWN;
        Player target = poll.getVotedPlayer();                      //copypaste everyfuckingwhere else
        for (Player pepe : players) {
            if (pepe instanceof Seer) {
                seeMe = ((Seer) pepe).revealPlayerAlignment(target);
            }
        }
    
        return new PlayerRevealedResult(target, seeMe);
    }
    
    /* (non-Javadoc)
     * @see phases.Phase#preparePoll(java.util.List)
     */
    @Override
    protected Poll preparePoll(List<Player> players) {
        List<Player> seers = new ArrayList<>();
        List<Player> alives = new ArrayList<>();
        for (Player numberOfPlayer : players) {
            if (numberOfPlayer.getStatus() != Player.PlayerStatus.DEAD) {
                alives.add(numberOfPlayer);
                if (numberOfPlayer instanceof Seer) {
                    seers.add(numberOfPlayer);
                }
            }
        }
        return new Poll(seers, alives);
    }
    
    /* (non-Javadoc)
     * @see phases.Phase#voteIsValid(roles.Player, roles.Player)
     */
    @Override
    protected boolean voteIsValid(Player voter, Player target) {
        //TODO Aufgabe 1b
        throw new UnsupportedOperationException("Not implemented yet!");
    }
}
