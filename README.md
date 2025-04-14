package biathlon;

import org.junit.jupiter.api.Test;

import java.util.Collections;
import java.util.List;

import static org.junit.jupiter.api.Assertions.*;

public class BiathlonTest {

    @Test
    public void testCSVParsingAndSorting() {
        String csv = """
            11,Umar Jorgson,SK,30:27,xxxox,xxxxx,xxoxo
            1,Jimmy Smiles,UK,29:15,xxoox,xooxo,xxxxo
            27,Piotr Smitzer,CZ,30:10,xxxxx,xxxxx,xxxxx
        """;

        List<Athlete> athletes = BiathlonParser.parse(csv);
        Collections.sort(athletes);

        assertEquals("Piotr Smitzer 30:10 (30:10 + 0)", athletes.get(0).toString());
        assertEquals("Jimmy Smiles 30:15 (29:15 + 60)", athletes.get(1).toString());
        assertEquals("Umar Jorgson 30:57 (30:27 + 30)", athletes.get(2).toString());
    }
}
