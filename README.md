# alexa-cta
A humble attempt at organizing thinking through a first Alexa skill.

## Info and Files Herein
- (Main JS file)
- (JSON)
- (Route Info)

## What Information Does the CTA Bus Tracker API Need?
When catching a bus, there are 4 potential variables:
- Route Number
- Route Direction
- Bus Stop Location
- Time

## Variables For Processing
- Route Number {rt}
  - Cardinal Direction {dir}
- Stop Location {loc}
- Time {t}

## Likely Reasonable Term Variations
How might we describe each of these?
<table>
					<thead>
						<tr>
							<th>Route {rt}</th>
							<th>Bus Stop {loc}</th>
							<th>Time {t}</th>
							<th>
                Direction {dir}</th>
						</tr>
					</thead>
					<tr>
						<td>
							<ul>
								<li>Numeric (eg 22, 6, 7, 8, etc)</li>
								<li>Alphanumeric (eg X9 bus, J48 bus, 8A, etc)</li>
								<li>Alphabetic (eg Ashland Express, Roosevelt bus, etc)</li>
								<li>Route Number via Route Destination {dir} Name (eg ‘Howard Terminal’ or ‘Clark/Harrison’ for the 22 North and 22 South buses)
									<ul>
										<li>Captures direction {dir}</li>
									</ul>
								</li>
							</ul>
						</td>
						<td>
							<ul>
								<li>Intersection (eg State and Lake)</li>
								<li>Incomplete intersection (eg State)</li>
								<li>Building (Art Institute)</li>
								<li>Stop ID (eg 75)</li>
								<li>Implied location (eg user context - stop closest to where you are when requesting information from Alexa - IP address)</li>
							</ul>
						</td>
						<td>
							<ul>
								<li>Complete time (eg 9:00 AM, 13:00)</li>
								<li>Incomplete time (eg 9:00, 8:00)</li>
								<li>Recency (eg ‘the next’)</li>
								<li>Broad time (eg ‘this morning’, ‘this afternoon’, etc)</li>
							</ul>								
						</td>
						<td>
							<ul>
								<li>Cardinal (eg north, south, east , west, northbound, etc)</li>
								<li>Destination Name
									<ul>
										<li>Route Destination (eg ‘Howard Terminal’ or ‘Clark/Harrison’ for the 22 North and 22 South buses)</li>
										<li>Other Geographic Destination (eg ‘towards downtown’, ‘away from downtown’, ‘to the loop’, etc)</li>
									</ul>	
								</li>
							</ul>
						</td>
					</tr>
				</table>

## Potential Query Combos
If we have 4 variables, what combinations of these variables are there?
<table>
	<thead>
		<tr>
			<th>Route +</th>
			<th>Route Direction +</th>
			<th>Bus Stop +</th>
			<th>Time =</th>
			<th>Result</th>
		</tr>
	</thead>
	<tr>							
		<td></td>
		<td></td>
		<td></td>
		<td></td>
		<td>{null}</td>
	</tr>
	<tr>							
		<td>{rt}</td>
		<td>{dir}</td>
		<td>{loc}</td>
		<td>{t}</td>
		<td>{rt,dir,loc,t}</td>
	</tr>
	<tr>
		<td>{rt}</td>
		<td>{dir}</td>
		<td>{loc}</td>
		<td></td>
		<td>{rt,dir,loc}</td>
	</tr>
	<tr>							
		<td>{rt}</td>
		<td>{dir}</td>
		<td></td>
		<td>{t}</td>
		<td>{rt,dir,t}</td>
	</tr>
	<tr>							
		<td>{rt}</td>
		<td></td>
		<td>{loc}</td>
		<td>{t}</td>
		<td>{rt,loc,t}</td>
	</tr>
	<tr>		
		<td></td>
		<td>{dir}</td>
		<td>{loc}</td>
		<td>{t}</td>
		<td>{dir,loc,t}</td>
	</tr>
	<tr>
		<td>{rt}</td>
		<td>{dir}</td>
		<td></td>
		<td></td>
		<td>{rt,dir}</td>
	</tr>
	<tr>							
		<td>{rt}</td>
		<td></td>
		<td>{loc}</td>
		<td></td>
		<td>{rt,loc}</td>
	</tr>
</table>
<table>
	<thead>
		<tr>	
			<th>Route +</th>
			<th>Route Direction +</th>
			<th>Bus Stop +</th>
			<th>Time =</th>
			<th>Result</th>
		</tr>							
	</thead>
	<tr>		
		<td>{rt}</td>
		<td></td>
		<td></td>
		<td>{t}</td>
		<td>{rt,t}</td>
	</tr>
	<tr>		
		<td></td>
		<td>{dir}</td>
		<td>{loc}</td>
		<td></td>
		<td>{dir,loc}</td>
	</tr>
	<tr>
		<td></td>
		<td>{dir}</td>
		<td></td>
		<td>{t}</td>
		<td>{dir,t}</td>
	</tr>
	<tr>	
		<td></td>
		<td></td>
		<td>{loc}</td>
		<td>{t}</td>
		<td>{loc,t}</td>
	</tr>
	<tr>
		<td>{rt}</td>
		<td></td>
		<td></td>
		<td></td>
		<td>{rt}</td>
	</tr>
	<tr>
		<td></td>
		<td>{dir}</td>
		<td></td>
		<td></td>
		<td>{dir}</td>
	</tr>
	<tr>
		<td></td>
		<td></td>
		<td>{loc}</td>
		<td></td>
		<td>{loc}</td>
	</tr>
	<tr>
		<td></td>
		<td></td>
		<td></td>
		<td>{t}</td>
		<td>{t}</td>
	</tr>
</table>

## Likely Reasonable Spoken Queries
<table>
    <thead>
        <tr>
            <th rowspan="2">Variable Combos</th>
            <th colspan="4">Missing Variable(s) Explicit and Implicit</th>
            <th rowspan="2">1st User Interaction (Rough Utterances)</th>
            <th rowspan="2">Sounds...</th>
            <th rowspan="2">Alexa 1st Reply</th>
        </tr>
        <tr>
            <th>rt</th>
            <th>dir</th>
            <th>loc</th>
            <th>t</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>{null}</td>
            <td>rt</td>
            <td>dir</td>
            <td>loc</td>
            <td>t</td>
            <td>
                <ol>
                    <li>Bus!</li>
                </ol>
            </td>
            <td>
                <ol>
                    <li>Silly</li>
                </ol>
            </td>
            <td>
                <ol>
                    <li>Go home human, you're drunk.</li>
                </ol>
            </td>
        </tr>
        <tr>
            <td>{rt,dir,loc,t}</td>
            <td>-</td>
            <td>-</td>
            <td>-</td>
            <td>-</td>
            <td>
                <ol>
                    <li>The number 999 northbound bus {rt}{dir} stops at State and Lake {loc} at 9:00AM {t}.</li>
                </ol>
            </td>
            <td>
                <ol>
                    <li>Silly</li>
                </ol>
            </td>
            <td>
                <ol>
                    <li>Great! Now get hopping!</li>
                </ol>
            </td>
        </tr>
        <tr>
            <td>{rt,dir,loc}</td>
            <td>-</td>
            <td>-</td>
            <td>-</td>
            <td>t</td>
            <td>
                <ol>
                    <li>What time {t} does the number 999 northbound bus {rt}{dir} stop at State and Lake {loc} ?</li>
                </ol>
            </td>
            <td>
                <ol>
                    <li>Ok</li>
                </ol>
            </td>
            <td>
                <ol>
                    <li>The next number 999 northbound bus stops at State and Lake at 11:00AM today.</li>
                </ol>
            </td>
        </tr>
        <tr>
            <td>{rt,dir,t}</td>
            <td>-</td>
            <td>-</td>
            <td>loc</td>
            <td>-</td>
            <td>
                <ol>
                    <li>Where {loc} does the number 999 northbound bus {rt}{dir} stop at 9:00 AM {t}?</li>
                </ol>
            </td>
            <td>
                <ol>
                    <li>Ok</li>
                </ol>
            </td>
            <td>
                <ol>
                    <li>The number 999 northbound bus stops at Clark and Addison at 9:00AM.</li>
                </ol>
            </td>
        </tr>
        <tr>
            <td>{rt,loc,t}</td>
            <td>-</td>            
            <td>dir</td>
            <td>-</td>
            <td>-</td>
            <td>
                <ol>
                    <li>Which direction {dir} number 999 bus {rt} stops at State and Lake {loc} at 9:00 AM {t}?</li>
                </ol>
            </td>
            <td>
                <ol>
                    <li>Ok</li>
                </ol>
            </td>
            <td>
                <ol>
                    <li>The number 999 northbound bus stops at State and Lake at 9:00AM.</li>
                </ol>
            </td>
        </tr>
        <tr>
            <td>{dir,loc,t}</td>
            <td>rt</td>
            <td>-</td>
            <td>-</td>
            <td>-</td>            
            <td>
                <ol>
                    <li>Which northbound {dir} bus {rt} stops at State and Lake {loc} at 9:00AM {t}?</li>
                </ol>
            </td>
            <td>
                <ol>
                    <li>Ok</li>
                </ol>
            </td>
            <td>
                <ol>
                    <li>The number 999 northbound bus stops at State and Lake at 9:00AM.</li>
                </ol>
            </td>
        </tr>
        <tr>
            <td>{rt,dir}</td>
            <td>-</td>
            <td>-</td>            
            <td>loc</td>
            <td>t</td>
            <td>
                <ol>
                    <li>Which busstop {loc} and what time {t} does the number 999 northbound bus {rt}{dir} stop at?</li>
                    <li>What time {t} does the number 999 northbound bus {rt}{dir} stop? {loc}</li>
                    <li>Which busstop {loc} does the number 999 northbound bus {rt}{dir} stop at? {t}</li>
                </ol>
            </td>
            <td>
                <ol>
                    <li>Silly</li>
                    <li>Ok-ish</li>
                    <li>Ok-ish</li>
                </ol>
            </td>
            <td>
                <ol>
                    <li>NA</li>
                    <li>Which busstop {loc} were you thinking of?</li>
                    <li>At what time {t} were you thinking?</li>
                </ol>
            </td>
        </tr>
        <tr>
            <td>{rt,loc}</td>
            <td>-</td>            
            <td>dir</td>
            <td>-</td>            
            <td>t</td>
            <td>
                <ol>
                    <li>What time {t} and what direction {dir} number 999 bus {rt} stops at State and Lake {loc}?</li>
                    <li>What time {t} does the number 999 bus {rt} stop at State and Lake {loc}? {dir}</li>
                    <li>What direction {dir} number 999 bus {rt} stops at State and Lake {loc}? {t}</li>
                </ol>
            </td>
            <td>
                <ol>
                    <li>Silly</li>
                    <li>Ok</li>
                    <li>Ok-ish</li>
                </ol>
            </td>
            <td>
                <ol>
                    <li>NA</li>
                    <li>Where you thinking about the x-bound {dir} or y-bound {dir} bus?</li>
                    <li>At what time {t} were you thinking?</li>
                </ol>
            </td>
        </tr>
        <tr>
          <td></td>
          <td></td>
          <td></td>
          <td></td>
          <td></td>
          <td></td>
          <td></td>
          <td></td>          
        </tr>
    </tbody>
</table>
