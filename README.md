<div tabindex="-1" id="notebook" class="border-box-sizing">

<div class="container" id="notebook-container">

<div class="cell border-box-sizing text_cell rendered">

<div class="inner_cell">

<div class="text_cell_render border-box-sizing rendered_html">

# Practical Data Science 2016, Assignment 2[¶](#Practical-Data-Science-2016,-Assignment-2)

In this assignment, you will follow the steps of researchers that investigated the value of personal connections in times of financial crisis.

* * *

> Panos Louridas, Associate Professor  
> Department of Management Science and Technology  
> Athens University of Economics and Business  
> louridas@aueb.gr

</div>

</div>

</div>

<div class="cell border-box-sizing text_cell rendered">

<div class="inner_cell">

<div class="text_cell_render border-box-sizing rendered_html">

In their paper [The value of connections in turbulent times: Evidence from the United States](http://dx.doi.org/10.1016/j.jfineco.2015.10.001), Daron Acemoglu, Simon Johnson, Amir Kermani, James Kwak, and Todd Mitton investigated whether firms that had personal connections with Timothy Geithner experienced an abnormal return when Geithner was appointed as U.S. Treasury Secretary on November 21, 2008.

Although replicating their full research is beyond the scope of a single assignment, you can follow a part of their argument.

At this point, read the paper, so that you know what we are talking about. Then come back and read the rest of the assignment. The paper is accessible from the AUEB network. If you are outside the AUEB network, you can still access it from [here](http://economics.mit.edu/files/11926). You can also find a version with additional material included as an appendix [here](https://pdfs.semanticscholar.org/2b6e/310d195a103377c9d7117ce27add691f18cb.pdf).

Now that you know what we are talking about, you will investigate the returns of the following firms:

<table>

<thead>

<tr>

<th>Firm</th>

</tr>

</thead>

<tbody>

<tr>

<td>BANK OF NY.MELLON CORP.</td>

</tr>

<tr>

<td>BEACON FED.BANC.INCORP.</td>

</tr>

<tr>

<td>BLACKROCK INCO.</td>

</tr>

<tr>

<td>CARVER BANCORP INCO.</td>

</tr>

<tr>

<td>CITI GROUP INCO.</td>

</tr>

<tr>

<td>CME GROUP INCO.</td>

</tr>

<tr>

<td>EVERCORE PARTNERS INCO.</td>

</tr>

<tr>

<td>FEDERATED INVRS.INCO.</td>

</tr>

<tr>

<td>FORTRESS INV.GP.LLC.</td>

</tr>

<tr>

<td>GAMCO INVESTORS INCO.</td>

</tr>

<tr>

<td>LAZARD LTD.</td>

</tr>

<tr>

<td>NORTHERN TRUST CORP.</td>

</tr>

<tr>

<td>POPULAR INCO.</td>

</tr>

<tr>

<td>PROVIDENT FINL.SVS.INCO.</td>

</tr>

<tr>

<td>STATE STREET CORP.</td>

</tr>

<tr>

<td>THE BLACKSTONE GROUP LP.</td>

</tr>

<tr>

<td>THE NASDAQ OMX GP.INCO.</td>

</tr>

</tbody>

</table>

The investigation will focus on the days following event day, where the event was Geithner's appointment: event day 0 was the day of the appointment, event day 1 was the following day, and so on.

</div>

</div>

</div>

<div class="cell border-box-sizing text_cell rendered">

<div class="inner_cell">

<div class="text_cell_render border-box-sizing rendered_html">

## Question 1[¶](#Question-1)

Investigate the returns of the selected companies compared to the returns of the S&P 500 index for event days 0, 1, ..., 10, and the cumulative returns for all event days 0 to 10\. So, you answer must include a table with a row for each of the event days and the cumulative result. It must also include columns for the set of the selected companies, the S&P 500, and the result of the statistical set that you used to determine the statistical significance between the two figures for each row. Your anwer will be similar in spirit to Table 2 of the original paper, however you will be using the whole S&P instead of the non-connected companies that is used there.

</div>

</div>

</div>

<div class="cell border-box-sizing text_cell rendered">

<div class="inner_cell">

<div class="text_cell_render border-box-sizing rendered_html">

## Question 2[¶](#Question-2)

The authors define the cumulative abnormal returns (CAR) of firm $i$ as:

$ \mathrm{CAR}[0, n]_i = \sum_{t=0}^{n}\mathrm{AR}_{it}$

where $\mathrm{CAR}[0, n]_i$ is the cumulative abnormal return for firm $i$ for event days 0 through $n$.

The term $\mathrm{AR}_{it}$ is calculated as follows:

$\mathrm{AR}_{it} = R_{it} - [\hat{\alpha_i} + \hat{\beta_i}R_{mt}]$

where $\mathrm{AR}_{it}$ is the abnormal return for firm $i$ on event day $t$, $R_{it}$ is the actual return on firm $i$ for event day $t$, and $R_{mt}$ is the return on the market for event day $t$, with the market return represented by the return on the S&P 500 index. Therefore to find $\mathrm{AR}_{it}$ you need to estimate $\hat{\alpha_i}$ and $\hat{\beta_i}$. You can do that by performing a regression:

$R_{it} = \alpha_i + \beta_iR_{mt} +\epsilon_{it}$

on a pre-event period of 250 trading days ending 30 days prior to event day 0.

After having obtained the $\mathrm{CAR}[0, n]_i$, you will estimate the following equation:

$\mathrm{CAR}_i = \alpha + \beta x_i + \epsilon_i$

where $\mathrm{CAR}_i$ is either $\mathrm{CAR}[0, 0]$, $\mathrm{CAR}[0, 1]$, or $\mathrm{CAR}[0, 10]$ for firm $i$, and $x_i$ is a measure of connections for firm $i$.

You will investigate two kinds of connections. First, you will investigate schedule connections, that is, connections that result from meetings between Geithner and people from the respective firms, as determined by the published Geithner daily schedule (made available after a Freedom of Information Act request). The number of schedule connections for each firm in the sample is in the following table:

<table>

<thead>

<tr>

<th>Firm</th>

<th>Schedule Connections</th>

</tr>

</thead>

<tbody>

<tr>

<td>BANK OF NY.MELLON CORP.</td>

<td>7</td>

</tr>

<tr>

<td>BEACON FED.BANC.INCORP.</td>

<td>1</td>

</tr>

<tr>

<td>BLACKROCK INCO.</td>

<td>13</td>

</tr>

<tr>

<td>CME GROUP INCO.</td>

<td>2</td>

</tr>

<tr>

<td>EVERCORE PARTNERS INCO.</td>

<td>1</td>

</tr>

<tr>

<td>FEDERATED INVRS.INCO.</td>

<td>1</td>

</tr>

<tr>

<td>LAZARD LTD.</td>

<td>1</td>

</tr>

<tr>

<td>NORTHERN TRUST CORP.</td>

<td>1</td>

</tr>

<tr>

<td>PROVIDENT FINL.SVS.INCO.</td>

<td>2</td>

</tr>

<tr>

<td>STATE STREET CORP.</td>

<td>1</td>

</tr>

<tr>

<td>THE BLACKSTONE GROUP LP.</td>

<td>6</td>

</tr>

<tr>

<td>THE NASDAQ OMX GP.INCO.</td>

<td>2</td>

</tr>

</tbody>

</table>

Second, you will investigate personal connections, that is, connections on a personal level (acquaintancies) between Geithner and the firms. The number of personal connections for each firm in the sample is in the following table:

<table>

<thead>

<tr>

<th>Firm</th>

<th>Personal Connections</th>

</tr>

</thead>

<tbody>

<tr>

<td>BLACKROCK INCO.</td>

<td>2</td>

</tr>

<tr>

<td>CARVER BANCORP INCO.</td>

<td>1</td>

</tr>

<tr>

<td>CITI GROUP INCO.</td>

<td>2</td>

</tr>

<tr>

<td>FORTRESS INV.GP.LLC.</td>

<td>1</td>

</tr>

<tr>

<td>GAMCO INVESTORS INCO.</td>

<td>1</td>

</tr>

<tr>

<td>POPULAR INCO.</td>

<td>1</td>

</tr>

<tr>

<td>THE BLACKSTONE GROUP LP.</td>

<td>4</td>

</tr>

<tr>

<td>THE NASDAQ OMX GP.INCO.</td>

<td>1</td>

</tr>

</tbody>

</table>

Your answer will include the estimate for $\beta$ when $x_i$ counts the schedule connections or when it counts the personal connections, when the dependent variable is $\mathrm{CAR}[0, 0]$, $\mathrm{CAR}[0, 1]$, or $\mathrm{CAR}[0, 10]$. Note: that means that you will run separate regressions for the schedule and the personal connections, in addition to the regressions for estimating $\hat{\alpha_i}$ and $\hat{\beta_i}$. Your anwer will be similar in spirit to Table 3 of the original paper.

</div>

</div>

</div>

<div class="cell border-box-sizing text_cell rendered">

<div class="inner_cell">

<div class="text_cell_render border-box-sizing rendered_html">

## Submission Instructions[¶](#Submission-Instructions)

You must submit your assignment as a Jupyter notebook that will contain the full code and documentation of how you solved the questions. The Jupyter notebook must be fully replicable: that is, somebody reading it must be able to do exactly what you did and obtain the same results.

For the market data, you can use any online source that you prefer, but make sure you document exactly how you got them.

_Only Jupyter submissions will be accepted. Do not submit plain Python code, they will not be graded at all._

</div>

</div>

</div>

<div class="cell border-box-sizing text_cell rendered">

<div class="inner_cell">

<div class="text_cell_render border-box-sizing rendered_html">

## Honor Code[¶](#Honor-Code)

You understand that this is an individual assignment, and as such you must carry it out alone. You may seek help on the Internet, by Googling or searching in StackOverflow for general questions pertaining to the use of Python and pandas libraries and idioms. However, it is not right to ask direct questions that relate to the assignment and where people will actually solve your problem by answering them. You may discuss with your fellow students in order to better understand the questions, if they are not clear enough, but you should not ask them to share their answers with you, or to help you by giving specific advice.

Keep in mind that this is so that _you_ should not waste your time and money on this course.

</div>

</div>

</div>

</div>

</div>
